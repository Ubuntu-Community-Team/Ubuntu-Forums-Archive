---
title: "Best way to override EDID"
date: 2012-06-22
forum: Desktop Environments
---

### Post by zasran on 2012-06-22
Using a notebook with HDMI 1.4 output and Dell U2711 monitor is a bit tricky, the monitor EDID info claims to be able to support resolutions up to 1920x1080 only.

Trial and error showed that I can override it using xrandr (note that frequency is only 40, any higher and monitor just goes blank):

xrandr --newmode "2560x1440_40.00"  201.00  2560 2720 2984 3408  1440 1443 1448 1476 -hsync +vsync

xrandr --addmode HDMI1 "2560x1440_40.00"

xrandr --output HDMI1 --mode 2560x1440_40.00

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) was pretty helpful in figuring this out, it's a bit less helpful in figuring out how to set this permanently.

Seems like best way is to include it in /etc/X11/xorg.conf but that is a bit tricky since I don't always use this monitor (computer is a notbook), I only want a new modeline to be applied everytime I connect the monitor.

Essentially I would like to override the EDID, it almost look like I should look into udev or something, not X windows.

I also see there are some settings conditionally applied (MatchProduct) but that only seems to be used for input devices.

Some people also recommend ~/.xprofile or ~/.xsession but that seems to be executed a bit late in the startup process plus these are not executed anymore. Even if they were still executed, I want the new mode set whenever I connect the monitor (might not be connected during startup).

Any recommendations on how to best accomplish this?

        erik

---

### Post by markbl on 2012-06-22
The edid in one of my 2 identical displays was corrupt for a couple of years but I got around it using the ignoreedid and customedid options that the nvidia proprietary driver provides. Since 12.04, like many others, I can not use the nvidia driver due to [obscene bug 973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096) so I must use the open nouveau driver which does not support those edid options.

So I wrote my [own edid-rw utility](https://github.com/bulletmark/edid-rw) to write a new edid to my monitor. Works well, so long as you are careful and know what you are doing.

---

### Post by zasran on 2012-06-22
thanks, edid-rw looks good but I am getting this error:

$ sudo ./edid-rw 0
Traceback (most recent call last):
  File "./edid-rw", line 76, in <module>
    main()
  File "./edid-rw", line 70, in main
    edid = [smb.read_byte_data(EDID_ADDR, i) for i in range(EDID_LEN)]
IOError: [Errno 12] Cannot allocate memory

This is: Ubuntu 12.04, Linux yummly-ubuntu-erik-gazelle 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Seems like 0 is the right number because 1 and higher numbers result in: IOError: [Errno 6] No such device or address

Tried with the monitor enabled and disabled, same result (it's an external monitor attached to a notebook).

Any ideas how to troubleshoot that?

---

### Post by markbl on 2012-06-22
> **zasran said:**
> 
This is: Ubuntu 12.04, Linux yummly-ubuntu-erik-gazelle 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Odd. Mine is a clean install of Ubuntu 12.04 with "Linux pc 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux" so is exactly the same, other than being 32 bit. The program is only trying to read 128 bytes so can't be a real memory allocation problem.

Googling finds [http://www.lm-sensors.org/ticket/645](http://www.lm-sensors.org/ticket/645) and [http://www.lm-sensors.org/ticket/625](http://www.lm-sensors.org/ticket/625) which seem to suggest your 64 bit kernel was not configured with the necessary "sysctl support". Sad.

---

### Post by zasran on 2012-06-28
Ok, it's pretty weird, when I run sudo edit-rw with argument 5, 6,7 8 I get valid results (piped to parse-edid it gives me what looks like valid info about monitors).

Values 5 and 6 both return exactly same EDID info for laptop LCD screen while values 7 and 8 both return info for the external monitor.

Now the question is how do I edit EDID? It seems there are no Linux tools, the only tool is Phoenix EDID tool. Is that what you used?

Any ideas about why do I get info for arguments 5 and 6 (LCD) and 7 and 8 (external monitor)? If I want to update external monitor should I write to 7 or 8? Both?

Also learned about i2cdetect but I don't see how it's output is related to edid-rw arguments 5, 6, 7, 8.

$ sudo i2cdetect -l
i2c-0	i2c       	i915 gmbus disabled             	I2C adapter
i2c-1	i2c       	i915 gmbus ssc                  	I2C adapter
i2c-2	i2c       	i915 GPIOB                      	I2C adapter
i2c-3	i2c       	i915 gmbus vga                  	I2C adapter
i2c-4	i2c       	i915 GPIOA                      	I2C adapter
i2c-5	i2c       	i915 gmbus panel                	I2C adapter
i2c-6	i2c       	i915 GPIOC                      	I2C adapter
i2c-7	i2c       	i915 gmbus dpc                  	I2C adapter
i2c-8	i2c       	i915 GPIOD                      	I2C adapter
i2c-9	i2c       	i915 gmbus dpb                  	I2C adapter
i2c-10	i2c       	i915 GPIOE                      	I2C adapter
i2c-11	i2c       	i915 gmbus reserved             	I2C adapter
i2c-12	i2c       	i915 gmbus dpd                  	I2C adapter
i2c-13	i2c       	i915 GPIOF                      	I2C adapter
i2c-14	i2c       	DPDDC-C                         	I2C adapter

Any pointers?

Alternatively: any ideas how to use KMS (kernel mode set) to update setting for specific monitor only? I only found how to update it for a given port (e.g. VGA1) but I only need the added mode for a specific monitor.

thanks,

        erik

---

### Post by markbl on 2012-06-29
> **zasran said:**
> Values 5 and 6 both return exactly same EDID info for laptop LCD screen while values 7 and 8 both return info for the external monitor.
That just means that is the address your monitors appear on the i2c bus. Read about the i2c bus on google.
> 
Now the question is how do I edit EDID? It seems there are no Linux tools, the only tool is Phoenix EDID tool. Is that what you used?
I already gave you the [ link](https://github.com/bulletmark/edid-rw) which describes what I used to edit my edid. Just my edid-rw utility, the parse-edid from the standard packages, and vim which is the standard linux editor (using xxd from within, see my comments in that [ link](https://github.com/bulletmark/edid-rw)).

---

### Post by humpty88 on 2013-03-10
I'd like to personally thank markbl for extending the life of my LCDmon, of which I would most likely would have junked it and bought a new one. It's a rather unique solution to what I admit is probably a rare event that your monitor's EDID goes corrupt on a distro's unwise design to depend on, to achieve a correct pixel resolution. But when it does happen, most non-geeky people would be brought to their knees to solve or suffer with a lower res. I could not find any other software solution that actually overwrites the EDID back to the actual monitor, most of the other workarounds are hacks to the system or driver. 
The correct checksum didn't perfectly repair the EDID but it did enable it to boot nicely and get rid of those dmesg errors.
Well done and thanks.

---

