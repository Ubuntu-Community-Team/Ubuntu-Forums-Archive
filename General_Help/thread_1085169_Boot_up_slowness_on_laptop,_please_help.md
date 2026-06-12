---
title: "Boot up slowness on laptop, please help"
date: 2009-03-02
forum: General Help
---

### Post by atippett on 2009-03-02
For some reason my system seems to hang in the boot process below.  I'm wondering if the time listed below is the time of when something starts or when it ends?  For example, is 45.238923] Adding 1748760k swap on /dev/sda3.  Priority:-1 extents:1 across:1748760k taking ~25 seconds?

Thanks for anyone's help and suggestions

```
[   12.986065] udev: renamed network interface wmaster0 to eth1
[   14.090749] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 17
[   14.101509] hda_intel: probe_mask set to 0x1 for device 17aa:2010
[   14.127942] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.004152] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.254750] input: TPPS/2 IBM TrackPoint as /class/input/input13
[   45.238923] Adding 1748760k swap on /dev/sda3.  Priority:-1 extents:1 across:1748760k
[   45.676987] EXT3 FS on sda1, internal journal
[   46.297084] loop: module loaded
[   46.417837] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taint
s kernel.
[   46.453226] [fglrx] Maximum main memory to use for locked dma buffers: 1887 MBytes.
[   46.468394] [fglrx]   vendor: 1002 device: 71d4 count: 1
[   46.483578] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   46.497815] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.512448] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   46.515737] [fglrx] Driver built-in PAT support is enabled successfully
[   46.527768] [fglrx] module loaded - fglrx 8.57.2 [Jan 14 2009] with 1 minors
[   46.821242] device-mapper: uevent: version 1.0.3
[   46.836722] device-mapper: ioctl: 4.13.0-ioctl (2007-10-18) initialised: dm-devel@redhat.com
[   47.176344] fuse init (API version 7.9)
[   56.906168] NET: Registered protocol family 10
[   56.918987] lo: Disabled Privacy Extensions

```

---

### Post by Geobot on 2009-03-03
The messages come up at different times, depending on when the script tells it to output. Some talk at the beginning, some at the end, some in the middle, etc. So it's hard to tell exactly this way.

As useful as the log is, I like using bootchart also. It outputs a graphical chart showing exactly how much time each process takes, so it shows it from another point of view.

Between the log and the bootchart, you can normally pinpoint what's taking up a lot of time. I mean, I've only been using Linux for a few months, and I was able to get my laptop's boot time down from 43 to 21 seconds(to gdm).

If I remember correctly, it's in the repositories, so just apt-get install bootchart

---

### Post by atippett on 2009-03-03
Here's my bootchart... looks like udevadm taking to long?

---

### Post by atippett on 2009-03-04
Getting some head way on this issue.  I removed splash=silent from grub on boot and found more detail:

[    9.607106] nsc-ircc, Found dongle: No dongle connected
[    9.612536] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060
)
[    9.612697] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.683306] Adding 1748760k swap on /dev/sda3.  Priority:-1 extents:1 acro
ss:1748760k

note the heartbeat=30 is the same amount of time that passes from that line to the next.

see threads:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=479381](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=479381)
[http://bugzilla.kernel.org/show_bug.cgi?id=10728](http://bugzilla.kernel.org/show_bug.cgi?id=10728)

---

### Post by atippett on 2009-03-04
Out of luck i moved on to a different issue because I couldn't figure out the slow bootup time.  I was tired of seeing wlan0_rename and thought the name was telling me to do something.. so i google and found people talking about slow boot times and issues with the udev file /etc/udev/rules.d/70-persistent-net.rules

People were saying to comment out the line with eth1
# PCI device 0x8086:0x4227 (ipw3945)
#SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:c5:7f:fc", NAME="eth1"


so I did and rebooted.  My boot time went from 64 seconds to 30 seconds.
Jeesh?  What just happened?

btw, my interface that was called wlan0_rename is now wlan0

---

### Post by pawett on 2010-07-08
Hello atippett,

thanks a lot for your last post!!!

After commenting out the line with ipw3945 in /etc/udev/rules.d/70-persistent-net.rules as described my laptop (FSC amilo) booted within less than 30s instead of 130s before. :D
I run debian 2.6.30-6 and the slow boot seemed to be related to udevadm according to bootchart. The boot process always stopped with the lines:[INDENT]Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.
[/INDENT]Also in my case the nasty wlan0_rename is replaced now by wlan0 .

---

