---
title: "1420N Lockup when using 3D Apps"
date: 2007-07-22
forum: Dell  Ubuntu Support
---

### Post by sciurus on 2007-07-22
Is anyone else experiencing this?

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104673](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104673)

I have an Inspiron 1420N with Ubuntu 7.04 installed by Dell. When I launch certain OpenGL applications (e.g. the screensaver Euphoria) X locks up. X does not respond to ctrl-alt-backspace and I cannot switch virtual terminals. I do stay logged in over ssh. The last entry in /var/log/messages is "[ 2674.200000] [drm:i915_wait_irq] *ERROR* i915_wait_irq: EBUSY -- rec: 34 emitted: 62". That last number, 62, varies.

If X was started by GDM, gdm detects that it locked up and restarts it. However, X does not start and gdm sits forever trying to start it. Stopping gdm and trying startx as root gives the following messages:
```

xauth: creating new authority file /home/brian/.serverauth.6778

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dell 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 22 22:15:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
Error in I830WaitLpRing(), now is 487836, start is 485835
pgetbl_ctl: 0x3ff80001 pgetbl_err: 0x0
ipeir: 0 iphdr: 0
LP ring tail: 48 head: 0 len: 1f001 start 0
eir: 0 esr: 0 emr: ffdf
instdone: 0 instpm: 0
memmode: 0 instps: 0
hwstam: dffe ier: a2 imr: 0 iir: 0
space: 130992 wanted 131064

Fatal server error:
lockup

Error in I830WaitLpRing(), now is 489844, start is 487843
pgetbl_ctl: 0x3ff80001 pgetbl_err: 0x0
ipeir: 0 iphdr: 0
LP ring tail: 50 head: 0 len: 1f001 start 0
eir: 0 esr: 0 emr: ffdf
instdone: 0 instpm: 0
memmode: 0 instps: 0
hwstam: dffe ier: a2 imr: 0 iir: 0
space: 130984 wanted 131064

FatalError re-entered, aborting
lockup

xinit: connection to X server lost.

waiting for X server to shut down

```

---

### Post by mcphargus on 2007-07-24
uninstall 915resolution, its installed by default, and it gives you a higher res at the expense of opengl

following that, install the xserver-xorg-video-intel  package and restart your xserver with ctrl+alt+backspace and you can get onto using the 1280 x 800 resolution

hopefully you didn't drop the extra 150 bucks or whatever it is for the hi def display, because i did and now I cant use it unless I dont want to use the notebook for the purpose for which i bought it: blender

compiz still won't work, by the way, we'll just have to wait and see what the community does in the way of improving the driver for the  open source x3100 display adapter, if anyone can figure anything out in the way of compiz with the x3100, post it loudly and proudly  and we'll all be in thy debt

---

### Post by notwen on 2007-07-24
> **mcphargus said:**
> if anyone can figure anything out in the way of compiz with the x3100, post it loudly and proudly  and we'll all be in thy debt

Cheers to that !!  Hope this is resolved by the time my dellbuntu arrives. =]

---

### Post by sciurus on 2007-07-24
[http://ubuntuforums.org/showthread.php?t=506744](http://ubuntuforums.org/showthread.php?t=506744)

---

### Post by nbubis on 2007-11-22
I'm having the same problem with the "new" intel driver on 7.10..
it seems that blender is trying to access non-existent memory on the g965 card, but playing around with the "videoram" parameter in xorg.conf hasn't helped yet.

the problem persists on blender 2.45 as well. any solutions??

---

### Post by Offoffoff on 2007-11-25
Blender 2.45. does not help me...

---

### Post by dpchemist on 2007-11-29
This bug is still here in Ubuntu 7.10 (on Thinkpad T61) !

Intel X3100 graphic card
Core Duo 2 GHz
Ubuntu 7.10
xserver-xorg-video-intel 2:2.1.1-0ubuntu9

It is even triggered by gnome-screensaver.

I have

[drm:i915_wait_irq] *ERROR* i915_wait_irq: EBUSY -- rec: 1810686 emitted: 1810707

in syslog

After that gdm tries to restart but hangs with a mouse cursor in the middle of the blank screen :-)

Any ideas hot to fix it?

---

