---
title: "NEED HELP resolution problems"
date: 2007-03-11
forum: Desktop Environments
---

### Post by LORD_PoLvO on 2007-03-11
hey guys i v badly need help, i been a long time ubuntu user and i have never had this problem.

i just booted my ubuntu system and it has started up in 800x600 resolution i cant change it using the screen res options and i cant even udjust res higher in any games i have tried taking to 800x600 option out of xrg and tht dosent make any difference can someone plz tell em whats going on and how i can fix it if there is a way  plz i really need help

---

### Post by matburton on 2007-03-11
What graphics card are you using?

Are other resolution options present but don't work?

---

### Post by toddedw on 2007-03-11
I'm having the same issue with a clean install of Ubuntu Linux Edgy (the disk was a month or two old though). After install on a Dell Dimension 2350 (Intel 845G/GL Onboard Graphics) I had all the resolutions I needed. I ran the updates, rebooted, and now the only option I have is 640x480. I would appreciate any help I got get.

Thanks

-- Todd

---

### Post by matburton on 2007-03-11
Right,

In xorg.conf (sudo gedit /etc/X11/xorg.conf) in the section that has 'Section "Device"' and then below Identifier "Intel bla bla bla" is it using the i810 Driver?

And in the same file in the Section "Screen" bit are all the resolutions your graphics card and screen supports present?

If so you may want to check out a package called 915resolution. It corrects the problem with most 800 or 900 Intel GMAs, I have the i915 chipset (900 GMA I think) and it worked for me!

Hope that helps,
Oh and you might have to add more package sources to find it if you haven't already.

---

### Post by toddedw on 2007-03-11
Yes and Yes, but I had a problem with the 915resolution.

todd@philomath:~$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
 915resolution
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1kB of archives.
After unpacking 131kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe 915resolution
0.5.2-4ubuntu1 [15.1kB]
Fetched 15.1kB in 1s (13.6kB/s)
Selecting previously deselected package 915resolution.
(Reading database ... 107692 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-4ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.2-4ubuntu1) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or
install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.

Should I sudo apt-get install vbetool?

---

### Post by matburton on 2007-03-11
Ok, what do you get when you try:
```
sudo /usr/sbin/915resolution -l
```

Do you get a list of modes with the correct resolutions?
Heres what I get:
> 
Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1680x1050, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1680x1050, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1680x1050, 32 bits/pixel


---

### Post by toddedw on 2007-03-11
todd@philomath:~$ sudo /usr/sbin/915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 3
Mode Table Offset: $C0000 + $4d2
Mode Table Entries: 25

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 48 : 1280x1024, 15 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

---

### Post by matburton on 2007-03-11
Are any of those the resolutions you want?

If so the auto configuration should just choose the resolution in your xorg.conf I'm guessing.

You could try this, open up this config file:
```
sudo gedit /etc/default/915resolution
```

MODE should be set to auto, if its not set it to auto and save

Otherwise pick a mode number that wasn't in your list (like 33) and set mode to that and then give it the right resolution and bit depth:
```

MODE=33
XRESO=1680
YRESO=1050
BIT=32
```

make sure you have this resolution in your xorg.conf as well!

and try that :-S hope your restarting between these attempts ;)

EDIT: auto may not help because it checks you cards BIOS which I'm guessing is the problem so I'd try making your own mode.

---

### Post by toddedw on 2007-03-11
No go. I tried 1025x768. I also changed my default depth in xorg.conf. Rebooting now.

---

### Post by matburton on 2007-03-11
Hmmm,

If you want 1024x768 maybe you should try simply overwriting the other one.
> 
MODE=54
XRESO=1024
YRESO=768
BIT=32


If that doesn't work then I'm out of my depth and google is your friend :(

---

### Post by toddedw on 2007-03-11
[http://ubuntuforums.org/showthread.php?p=1900323](http://ubuntuforums.org/showthread.php?p=1900323)

Found this on my graphics card.

EDIT: The problem with my Intel 82845G/GL[Brookdale-G] is now fixed. I added the VideoRAM line to my /etc/X11/xorg.conf. Apparently it wasn't getting enough memory and defaulting to 640x480. I hope this helps people out.

> 
Section "Device"
Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics D$
Driver          "i810"
BusID           "PCI:0:2:0"
VideoRAM        32768
EndSection


---

### Post by LORD_PoLvO on 2007-03-11
im using an Nvidia Geforce 6200 i used ```
sudo dpkg-reconfigure xserver-xorg
``` i set my driver to NV (the non acellerated nvidia driver) and it booted up fine when i set the driver to nvidia gdm failed to start using ```
/etc/init.d/gdm start
```

but opened with nv??

but when i turned my pc on this morning it booted with the nvidia driver no probelms does ne1 know what going on ??

---

