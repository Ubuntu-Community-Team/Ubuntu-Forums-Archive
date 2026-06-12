---
title: "[SOLVED] ALPs touchpad scroll stopped working, 8.04, XPS M1530 N Series"
date: 2009-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dphurst on 2009-01-09
The ALPS touchpad does not vertically scroll. The Xorg.0.log shows that the Synaptics Touchpad is not found. The evdev driver is loaded. SHMConfig is true in my xorg.conf. I have the kernel option i8402.nomux=1 in the menu.lst file as stated.

The machine is a XPS M1530 N series just acquired from Dell with 8.04 preinstalled but not 8.04.1. Initially the touchpad vertical scroll worked when the laptop was first booted. The Ubuntu updates that were required to bring the laptop up to date broke the touchpad scrolling. I tried fixing it by switching kernels from the generic to the 386. That actually worked, yet lost the multi-core functionality. Anyway, I'm back to the generic kernel.

Any ideas on why the synaptics touchpad driver isn't loaded? I've read quite a bit of different threads on this topic. Some are fixed by modifying and rebuilding the alps driver. Others are fixed with kernel option mentioned above.
Thanks for your help,
Dow

---

### Post by namdung on 2009-01-09
In *System==>Pref==>Mouse==>Touchpad*, select *Enable Touchpad*.

---

### Post by dphurst on 2009-01-09
The fix that worked is to not allow the psmouse module to load before the alps module.

See this thread for the fix:
[http://ubuntuforums.org/showthread.php?t=808164&highlight=alps+scroll&page=3](http://ubuntuforums.org/showthread.php?t=808164&highlight=alps+scroll&page=3)

I tested the fix this way:

In a shell:
[B]sudo rmmod psmouse && modprobe psmouse
[/B]
log out of the graphical interface

use **Ctl-Alt-Backspace** to restart the X server while your at the login screen.

log back in to the graphical interface and test the touchpad for scrolling functionality.  If this works then apply the fix as follows:

Blacklist the psmouse module by making a file in /etc/modprobe.d. I called mine touchpad, but the way I understand it, you can call it anything you want. Running an LS will show that there are blacklists in this folder. We're going to blacklist the psmouse module at boot up.

[B]cd /etc/modprobe.d
sudo gedit touchpad[/B]

with the new file open type one line:

**blacklist psmouse**

Save and exit. This will keep the psmouse module from loading before the synaptics drivers. Now your touchpad will have its full functionality. But be careful and hope your power doesn't fail, because without this module your touchpad won't work at all. So you need to load it with a command that runs after boot. Fortunately Ubuntu has created a nifty device for such things called rc.local. After making sure your rc.local file is executable, you need to add modprobe psmouse to it before the exit 0 line.


[B]cd /etc
ls -lah rc.local[/B]
-rwxr-xr-x 1 root root 306 2008-04-22 10:49 rc.local
**sudo gedit rc.local**

When your done it should look something like:

[B]modprobe psmouse
exit 0[/B]


You're done! Reboot and see if your touchpad scroll or other things are working. If you have SHMConfig in your xorg.conf, check to see if it's also enabled.

---

### Post by oooh on 2010-06-14
I am trying to do that, but there is no EXIT 0 in my rc.local file 

Any idea?

---

### Post by oooh on 2010-06-14
Ok, tried out, I just added the line in here:

```
sudo modprobe psmouse proto=imps
exit 0
```

At the end of the file, and psmouse is nicely loaded. However I still can not scroll. I believe it is a problem with the hardware, as I can not load it, according to /var/log/Xorg.0.log:

```

(II) Synaptics touchpad driver version 1.2.2
Synaptics Touchpad no synaptics event device found
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(--) Synaptics Touchpad: no supported touchpad found
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

```

---

