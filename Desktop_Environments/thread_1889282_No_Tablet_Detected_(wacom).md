---
title: "No Tablet Detected (wacom)"
date: 2011-12-01
forum: Desktop Environments
---

### Post by manitislate on 2011-12-01
I've tried so many things and read so much, I can't figure this out.

I've been trying to use my Wacom Intuos 2 tablet on an Ubuntu 11.10 system (intel core 2 quad). The tablet uses a usb connection.

I start up "wacom graphics tablet" under "system settings" and it says "No tablet detected. please plug in or turn on your wacom tablet."


I'm lost....
don't know what to do...
some one....
please help...:confused:

---

### Post by Favux on 2011-12-01
Hi manitislate,

Welcome to Ubuntu forums!

It should work out of the box as you know.

Do the following with it plugged in.  Run these commands in a terminal and post the outputs.
```
lsusb | grep Wacom
```
and
```
xinput list
```
and
```
lsmod | grep wacom
```

---

### Post by manitislate on 2011-12-01
Hi Favux,

Thanks so so much for your help. :)


> **Favux said:**
> 
```
lsusb | grep Wacom
```
```
Bus 004 Device 002: ID 056a:0045 Wacom Co., Ltd Intuos2 12x18
```

> **Favux said:**
> 
```
xinput list
```
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Media Center Ed. eHome Infrared Remote Transceiver (04eb:e004)	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]

```

> **Favux said:**
> 
```
lsmod | grep wacom
```
```
wacom                  37975  0 
```

---

### Post by Favux on 2011-12-01
Alright, the lsusb confirms it is a usb tablet and the system sees it.  The lsmod shows the Wacom usb kernel driver is autoloading.  But xinput doesn't show the tablet, which it should.  So that pretty much leaves the Wacom X driver or the match in the 50-wacom.conf to it.

Is the package xserver-xorg-input-wacom installed on your system?  It should be by default.

---

### Post by manitislate on 2011-12-01
> **Favux said:**
> Alright, the lsusb confirms it is a usb tablet and the system sees it.  The lsmod shows the Wacom usb kernel driver is autoloading.  But xinput doesn't show the tablet, which it should.  So that pretty much leaves the Wacom X driver or the match in the 50-wacom.conf to it.

Is the package xserver-xorg-input-wacom installed on your system?  It should be by default.

No it is not. I've been trying to get that to install using software center, but I get an error: "Failed to download package files: check your internet connection."

---

### Post by Favux on 2011-12-01
What happens if you try it from the command line?
```
sudo apt-get install xserver-xorg-input-wacom
```

---

### Post by manitislate on 2011-12-01
> **Favux said:**
> What happens if you try it from the command line?
```
sudo apt-get install xserver-xorg-input-wacom
```

sweet...it installed just fine:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xorg-input-wacom
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 97.2 kB of archives.
After this operation, 328 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xserver-xorg-input-wacom
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net/irie/wacom/ubuntu/ natty/main xserver-xorg-input-wacom amd64 1:0.11.99+git20111013-0irie1~natty1 [97.2 kB]
Fetched 97.2 kB in 1s (66.0 kB/s)                   
Selecting previously deselected package xserver-xorg-input-wacom.
(Reading database ... 278129 files and directories currently installed.)
Unpacking xserver-xorg-input-wacom (from .../xserver-xorg-input-wacom_1%3a0.11.99+git20111013-0irie1~natty1_amd64.deb) ...
Processing triggers for man-db ...
Setting up xserver-xorg-input-wacom (1:0.11.99+git20111013-0irie1~natty1) ...
```

I knew I would need to log off, so I just went ahead and did a complete restart, and it worked. :)

I was wondering if I should also install wacom-tools? And would it go something like this?
```
sudo apt-get install wacom-tools
```

---

### Post by Favux on 2011-12-01
Wacom-tools is no more.  That was when there was linuxwacom.  Now the wacom package contains xf86-input-wacom, which is the X driver.  The most important part of wacom-tools, xsetwacom, is included with xf86-input-wacom.

The Wacom tablet applet in System Settings is the first tentative replacement for the old wacomcpl (wacom control panel) that was in wacom-tools.

---

### Post by manitislate on 2011-12-02
> **Favux said:**
> Wacom-tools is no more.  That was when there was linuxwacom.  Now the wacom package contains xf86-input-wacom, which is the X driver.  The most important part of wacom-tools, xsetwacom, is included with xf86-input-wacom.

The Wacom tablet applet in System Settings is the first tentative replacement for the old wacomcpl (wacom control panel) that was in wacom-tools.

sweet.

Thank you, thank you, thank you so much :) I love the Ubuntu community just as much as I love my Ubuntu system.

---

### Post by mcblades on 2011-12-18
Hi:  

I am having a kind of similar problem trying to get a 6x8 intuos 2 to work in ubuntu 11.10.  When I plug in the tablet it seems that it is being detected by X but neither the pen or the mouse work.  This happens whether I plug in the tablet after bootup or restart with it plugged in.  

This is the output of lsusb | grep wacom

```
mark@server1:~$ lsusb | grep Wacom
Bus 002 Device 005: ID 056a:0042 Wacom Co., Ltd Intuos2 6x8
mark@server1:~$ 

```and xinput list gives:
```
mark@server1:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Generic Explorer Mouse             id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 6x8 stylus                    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 6x8 eraser                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 6x8 cursor                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
mark@server1:~$ 
```lsmod | grep wacom gives
```
mark@server1:~$ lsmod | grep wacom
wacom                  37007  0 
```also:
```
mark@server1:~$ sudo apt-get install xserver-xorg-input-wacom
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-wacom is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
```I have looked at Xorg.0.log and the tablet seems to be being detected when I plug it in:
```
[   386.682] (II) config/udev: Adding input device Wacom Intuos2 6x8 (/dev/input/event3)
[   386.682] (**) Wacom Intuos2 6x8: Applying InputClass "evdev tablet catchall"
[   386.682] (**) Wacom Intuos2 6x8: Applying InputClass "Wacom class"
[   386.682] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8'
[   386.682] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   386.682] (**) Wacom Intuos2 6x8: always reports core events
[   386.682] (**) Option "Device" "/dev/input/event3"
[   386.682] (II) Wacom Intuos2 6x8: type not specified, assuming 'stylus'.
[   386.682] (II) Wacom Intuos2 6x8: other types will be automatically added.
[   386.682] (--) Wacom Intuos2 6x8 stylus: using pressure threshold of 27 for button 1
[   386.682] (--) Wacom Intuos2 6x8 stylus: Wacom USB Intuos2 tablet maxX=20320 maxY=16240 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[   386.682] (II) Wacom Intuos2 6x8 stylus: hotplugging dependent devices.
[   386.682] (II) Wacom Intuos2 6x8 stylus: hotplugging completed.
[   386.720] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.6/2-4.6:1.0/input/input5/event3"
[   386.720] (II) XINPUT: Adding extended input device "Wacom Intuos2 6x8 stylus" (type: STYLUS)
[   386.720] (**) Wacom Intuos2 6x8 stylus: (accel) keeping acceleration scheme 1
[   386.720] (**) Wacom Intuos2 6x8 stylus: (accel) acceleration profile 0
[   386.720] (**) Wacom Intuos2 6x8 stylus: (accel) acceleration factor: 2.000
[   386.720] (**) Wacom Intuos2 6x8 stylus: (accel) acceleration threshold: 4
[   386.720] (**) Wacom Intuos2 6x8 eraser: Applying InputClass "evdev tablet catchall"
[   386.720] (**) Wacom Intuos2 6x8 eraser: Applying InputClass "Wacom class"
[   386.720] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8 eraser'
[   386.720] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   386.720] (**) Wacom Intuos2 6x8 eraser: always reports core events
[   386.720] (**) Option "Device" "/dev/input/event3"
[   386.720] (--) Wacom Intuos2 6x8 eraser: Wacom USB Intuos2 tablet maxX=20320 maxY=16240 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[   386.736] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.6/2-4.6:1.0/input/input5/event3"
[   386.736] (II) XINPUT: Adding extended input device "Wacom Intuos2 6x8 eraser" (type: ERASER)
[   386.736] (**) Wacom Intuos2 6x8 eraser: (accel) keeping acceleration scheme 1
[   386.736] (**) Wacom Intuos2 6x8 eraser: (accel) acceleration profile 0
[   386.736] (**) Wacom Intuos2 6x8 eraser: (accel) acceleration factor: 2.000
[   386.736] (**) Wacom Intuos2 6x8 eraser: (accel) acceleration threshold: 4
[   386.736] (**) Wacom Intuos2 6x8 cursor: Applying InputClass "evdev tablet catchall"
[   386.736] (**) Wacom Intuos2 6x8 cursor: Applying InputClass "Wacom class"
[   386.736] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8 cursor'
[   386.736] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   386.736] (**) Wacom Intuos2 6x8 cursor: always reports core events
[   386.736] (**) Option "Device" "/dev/input/event3"
[   386.736] (--) Wacom Intuos2 6x8 cursor: Wacom USB Intuos2 tablet maxX=20320 maxY=16240 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[   386.760] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.6/2-4.6:1.0/input/input5/event3"
[   386.760] (II) XINPUT: Adding extended input device "Wacom Intuos2 6x8 cursor" (type: CURSOR)
[   386.760] (**) Wacom Intuos2 6x8 cursor: (accel) keeping acceleration scheme 1
[   386.760] (**) Wacom Intuos2 6x8 cursor: (accel) acceleration profile 0
[   386.760] (**) Wacom Intuos2 6x8 cursor: (accel) acceleration factor: 2.000
[   386.760] (**) Wacom Intuos2 6x8 cursor: (accel) acceleration threshold: 4
[   386.760] (II) config/udev: Adding input device Wacom Intuos2 6x8 (/dev/input/mouse0)
[   386.760] (II) No input driver/identifier specified (ignoring)
```I also noticed the following streams of errors occuring when the mouse is placed on the tablet (this error doesn't always occur though?
```
[   376.993] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   376.997] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   377.001] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   377.005] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   377.013] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
```I hope somebody can help as I am at my wits end with this.

thanks in advance

Mark

---

### Post by Favux on 2011-12-18
Hi Mark,

Welcome to Ubuntu forums!

So this is one of the earliest usb tablets, since the first Intuos2's were serial.

Everything looks OK, as long as there is no error later in Xorg.0.log where the wacom module is unloaded.  The error you are seeing makes it sound like the driver doesn't think your Wacom mouse (cursor) is returning a valid serial number.  You're not seeing that with stylus are you?

Let's take a look at your 50-wacom.conf in /usr/share/X11/xorg.conf.d just in case.  Also if you look at *man xsetwacom* in a terminal it describes two xsetwacom debug parameters you could use, one is tablet wide and one for the specific input tool.  You can use both at once.  That might show more about what's going on.

My first thought is to go ahead and update xf86-input-wacom from the Oneiric default 0.11.0 to the recently released 0.12.0 and see if that makes a difference.  Part II. in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by mcblades on 2011-12-18
Hi Favux,  Thank you so much for helping me sort this out.  I have had the tablet for a while but haven't been able to use it since upgrading to ubuntu a couple of years ago. 


this is the output from the 50-wacom.conf
```
mark@server1:~$ cat /usr/share/X11/xorg.conf.d/50-wacom.conf 
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WALTOP|WACOM|Hanwang|ISD-V4"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

```I think I was seeing the error with both pen and mouse.  Will try and replicate and get back to you.  USB Parse Error only occurs if tablet is plugged in at startup and occurs with both pen and mouse.  If tablet is plugged in after or unplugged and plugged back in then no error but also no respoinse to mouse or pen.

---

### Post by Favux on 2011-12-18
Alright, see if updating the X driver helps.

I think I've seen this before and our "fix" was to use a xorg.conf instead of the .conf (which is fine by the way) in xorg.conf.d.  If you have a xorg.conf what are the contents?

---

### Post by mcblades on 2011-12-18
Right,  I followed the instructions to clone the git repository etc. updated X and rebooted. running a git pull shows xf86-input-wacom as already up to date.

Still got the same problems though.  Also, rechecked and it is the mouse only causing the USB Parse error and only when plugged in at reboot.  Hotplug causes the mouse to be ignored also.  The pen has no effect in either situation.

I don't seem to have an xorg.conf.d directory or an xorg.conf file  I have tried find xorg.conf to no avail.  also looked in /etc/X11/ and usr/etc/X11  

Where else should I look?

---

### Post by Favux on 2011-12-18
If it was there it would be in /etc/X11.  We'll make one.  Just be ready to repair things from the command line if we break X.

Does the tablet have a pad?  Tablet buttons or ExpressKeys in other words.

---

### Post by mcblades on 2011-12-18
Found it in here, here's the output

```
mark@server1:/usr/share/X11/xorg.conf.d$ cat 50-wacom.conf
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM|WALTOP|Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

```

---

### Post by mcblades on 2011-12-18
The tablet has no "clickable" buttons.  There is a row of "function key" hotspots at the top of the pad with the numbers 1-13 and commands like new open close save etc.. ending with mode  pen|mouse and pressure soft|medium|hard.

---

### Post by Favux on 2011-12-18
Alright, that's what I thought.

So to create the xorg.conf file use:
```
gksudo gedit /etc/X11/xorg.conf
```
Then copy and paste the following into it:
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"        # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                      # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"        # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                      # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"                                  # Wacom tablet mouse
  Option        "Device"        "/dev/input/wacom"        # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                      # USB ONLY
EndSection

Section "ServerLayout"
  Identifier    "X.org Configured"
  InputDevice   "stylus"
  InputDevice   "eraser"
  InputDevice   "cursor"     # For non-LCD tablets only
EndSection
```
Whatever runs last controls.  And xorg.conf runs after xorg.conf.d so it takes precedent over the 50-wacom.conf in xorg.conf.d.

I checked the 69-xserver-xorg-input-wacom.rules file in /lib/udev/rules.d and your model is there:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0042", SYMLINK+="input/tablet-intuos2-6x8"
```
So the wacom symlink should work.

---

### Post by mcblades on 2011-12-18
Added the lines to xorg.xconf

rebooted with the tablet plugged in and got the USB parse error again.
unplugged the tablet and got ```

[   415.556] (EE) Wacom Intuos2 6x8 cursor: Error reading wacom device : No such device
[   415.556] (EE) Wacom Intuos2 6x8 cursor: Error reading wacom device : No such device
[   415.556] (EE) Wacom Intuos2 6x8 cursor: Error reading wacom device : No such device
[   415.556] (EE) Wacom Intuos2 6x8 cursor: Error reading wacom device : No such device
[   415.556] (EE) Wacom Intuos2 6x8 cursor: Error reading wacom device : No such device
[   415.556] (EE) Wacom Intuos2 6x8 cursor: Error reading wacom device : No such device 
```then the computer rebooted. I rebooted without the tablet plugged in.  After plugging in the tablet i got this:

```
[   366.705] (II) config/udev: Adding input device Wacom Intuos2 6x8 (/dev/input/mouse1)
[   366.705] (II) No input driver/identifier specified (ignoring)
[   366.706] (II) config/udev: Adding input device Wacom Intuos2 6x8 (/dev/input/event4)
[   366.706] (**) Wacom Intuos2 6x8: Applying InputClass "evdev tablet catchall"
[   366.706] (**) Wacom Intuos2 6x8: Applying InputClass "Wacom class"
[   366.706] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8'
[   366.706] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   366.706] (**) Wacom Intuos2 6x8: always reports core events
[   366.706] (**) Option "Device" "/dev/input/event4"
[   366.706] (II) Wacom Intuos2 6x8: type not specified, assuming 'stylus'.
[   366.706] (II) Wacom Intuos2 6x8: other types will be automatically added.
[   366.706] (--) Wacom Intuos2 6x8 stylus: using pressure threshold of 27 for button 1
[   366.706] (--) Wacom Intuos2 6x8 stylus: Wacom USB Intuos2 tablet maxX=20320 maxY=16240 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[   366.706] (II) Wacom Intuos2 6x8 stylus: hotplugging dependent devices.
[   366.706] (EE) Wacom Intuos2 6x8 stylus: Invalid type 'touch' for this device.
[   366.706] (EE) Wacom Intuos2 6x8 stylus: Invalid type 'pad' for this device.
[   366.706] (II) Wacom Intuos2 6x8 stylus: hotplugging completed.
[   366.732] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.6/2-4.6:1.0/input/input4/event4"
[   366.732] (II) XINPUT: Adding extended input device "Wacom Intuos2 6x8 stylus" (type: STYLUS)
[   366.732] (**) Wacom Intuos2 6x8 stylus: (accel) keeping acceleration scheme 1
[   366.732] (**) Wacom Intuos2 6x8 stylus: (accel) acceleration profile 0
[   366.732] (**) Wacom Intuos2 6x8 stylus: (accel) acceleration factor: 2.000
[   366.732] (**) Wacom Intuos2 6x8 stylus: (accel) acceleration threshold: 4
[   366.732] (**) Wacom Intuos2 6x8 eraser: Applying InputClass "evdev tablet catchall"
[   366.732] (**) Wacom Intuos2 6x8 eraser: Applying InputClass "Wacom class"
[   366.732] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8 eraser'
[   366.732] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   366.732] (**) Wacom Intuos2 6x8 eraser: always reports core events
[   366.732] (**) Option "Device" "/dev/input/event4"
[   366.732] (**) Option "Type" "eraser"
[   366.732] (--) Wacom Intuos2 6x8 eraser: Wacom USB Intuos2 tablet maxX=20320 maxY=16240 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[   366.744] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.6/2-4.6:1.0/input/input4/event4"
[   366.744] (II) XINPUT: Adding extended input device "Wacom Intuos2 6x8 eraser" (type: ERASER)
[   366.744] (**) Wacom Intuos2 6x8 eraser: (accel) keeping acceleration scheme 1
[   366.744] (**) Wacom Intuos2 6x8 eraser: (accel) acceleration profile 0
[   366.744] (**) Wacom Intuos2 6x8 eraser: (accel) acceleration factor: 2.000
[   366.744] (**) Wacom Intuos2 6x8 eraser: (accel) acceleration threshold: 4
[   366.744] (**) Wacom Intuos2 6x8 cursor: Applying InputClass "evdev tablet catchall"
[   366.744] (**) Wacom Intuos2 6x8 cursor: Applying InputClass "Wacom class"
[   366.744] (II) Using input driver 'wacom' for 'Wacom Intuos2 6x8 cursor'
[   366.744] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   366.744] (**) Wacom Intuos2 6x8 cursor: always reports core events
[   366.744] (**) Option "Device" "/dev/input/event4"
[   366.744] (**) Option "Type" "cursor"
[   366.744] (--) Wacom Intuos2 6x8 cursor: Wacom USB Intuos2 tablet maxX=20320 maxY=16240 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[   366.752] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.6/2-4.6:1.0/input/input4/event4"
[   366.752] (II) XINPUT: Adding extended input device "Wacom Intuos2 6x8 cursor" (type: CURSOR)
[   366.752] (**) Wacom Intuos2 6x8 cursor: (accel) keeping acceleration scheme 1
[   366.752] (**) Wacom Intuos2 6x8 cursor: (accel) acceleration profile 0
[   366.752] (**) Wacom Intuos2 6x8 cursor: (accel) acceleration factor: 2.000
[   366.752] (**) Wacom Intuos2 6x8 cursor: (accel) acceleration threshold: 4
[   392.722] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   392.730] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   392.734] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
[   392.738] (EE) Wacom Intuos2 6x8 cursor: usbParse: Ignoring event from invalid serial 0
```  which I suppose is an improvement over not being recognised after hotplug.

unplugging the tablet worked this time, which was a relief.
```
[   415.556] (II) config/udev: removing device Wacom Intuos2 6x8 stylus
[   415.557] (II) UnloadModule: "wacom"
[   415.557] (II) Unloading wacom
[   415.557] (II) config/udev: removing device Wacom Intuos2 6x8 eraser
[   415.557] (II) UnloadModule: "wacom"
[   415.557] (II) Unloading wacom
[   415.557] (II) config/udev: removing device Wacom Intuos2 6x8 cursor
[   415.569] (II) UnloadModule: "wacom"
[   415.569] (II) Unloading wacom

```

---

### Post by Favux on 2011-12-18
OK, so adding a xorg.conf did change the behavior a little.  Which it really shouldn't.  Slightly different code path?  For instance the xorg.conf doesn't work with hot plugging, hence the xorg.conf.d.

Stylus still isn't working I gather.

It seems like they've inadvertently broken the code for the usb Intuos2.  That could be caused by any number of things.  The developers seem to tend to have Intuos4's or BambooPT's so they might not catch something like that.  So a possible question is, is the usb protocol for an Intuos2 just a little different from later models, maybe still using some sort of protocol V holdover from the serial version?  You could try posting on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)  and see if you can get a developer interested in looking at it.  Because like I said I seem to remember a couple of other early models also having trouble (maybe in Natty?).  You'd probably have to be willing to do diagnostics they ask for.

One other thing complicating the situation in Oneiric is Oneiric has Gnome 3.2.  Which means the first version of the Wacom tablet applet in System Settings.  That uses some, but not all of the Wacom hooks, added to the gnome-settings-daemon.  The rest of the key values can be accessed with dconf-editor.  The key values will override anything in xorg.conf.d or xorg.conf.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  But I don't think anything in there would be causing this trouble.

Not sure why a parse error with the cursor would also knock out the stylus.  I'll see if anything jumps out at me in wcmValidateDevice.c or something.

Edit:  I do wonder about wcmValidateDevice.c, for example this function around line 500:
```
/**
 * Hotplug all serial numbers configured on this device.
 *
 * @param basename The kernel device name
 */
static void wcmHotplugSerials(InputInfoPtr pInfo, const char *basename)
{
	WacomDevicePtr  priv = (WacomDevicePtr)pInfo->private;
	WacomCommonPtr  common = priv->common;
	WacomToolPtr    ser = common->serials;

	while (ser)
	{
		xf86Msg(X_INFO, "%s: hotplugging serial %d.\n", pInfo->name, ser->serial);

		if (wcmIsAValidType(pInfo, "stylus") &&
		    (ser->typeid & STYLUS_ID))
			wcmQueueHotplug(pInfo, basename, "stylus", ser->serial);

		if (wcmIsAValidType(pInfo, "eraser") &&
		    (ser->typeid & ERASER_ID))
			wcmQueueHotplug(pInfo, basename, "eraser", ser->serial);

		if (wcmIsAValidType(pInfo, "cursor") &&
		    (ser->typeid & CURSOR_ID))
			wcmQueueHotplug(pInfo, basename, "cursor", ser->serial);

		ser = ser->next;
	}
}
```
Which is part of the chain initializing the input tools.

---

### Post by mcblades on 2011-12-18
Thanks for all the help so far.  Incidentally, I tried the tablet on  a vanilla oneiric install and got the same errors so I don't think it is my organically grown ubuntu (updated and upgraded from intrepid) that's caused the problem. I guess  I may end up having to buy a new tablet, but I want to be sure I get one that will work without too much hair pulling.

thanks again, it's people like you that make Linux such a nice place to be!

Mark

---

