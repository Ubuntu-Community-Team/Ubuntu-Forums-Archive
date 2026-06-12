---
title: "Desktop effects, glx and nvidiadrivers (8500GT)"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by Thorning on 2008-01-22
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=618021](http://ubuntuforums.org/showthread.php?t=618021) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello.
This is my first post, I'm new to linux, so, have mercy..
I love ubuntu so far. I installed the 7.10 desktop version recently and so far I'm happy... It appears to be very thought-through. After some tweaking everything works, and I mean everything down to the mobile phone and my EMS2-adaptor which I didn't even expect.
Very nice and creds to all of you ubuntu developers!

...except the desktop effects.

Ok, so this is my problem:
When trying to activate the effects the system asks me to please install the glx-nvidia-new drivers. Ok, fine. 
However, when I do install them all my openGL functions stop working and nvidia-settings reporting back "Fail to query the GLX server vendor".
This is very similar to the "3D Effects with Nvidia geForce 8500GT.. HELP..."-topic (related link) but not exactly. My openGL works as far as I can tell, as long as I don't install any glx driver. I can use any openGL related program/test/screensaver except for the visual desktop effects.
Allso, my display does not stop working after installing nvidia-glx-new driver as many others experience. No, only the openGL function stops working.

So it seems like nvidia-glx-new driver (which definitly should be the correct one to use since the card is so new) is not compatible with my vendor(?) or what?

Useful info:
glxgears reports: 43302 frames in 5.0 seconds = 8660.331 FPS (So it works (?) At least I'm happy)

I use a Viewsonic Q22wb monitor on a built-in GeForce 6100
and a Hitachi CM721F monitor on a pci-e connected GeForce 8500GT

My xorg.conf:

---

### Post by chewearn on 2008-01-23
Could it be related to the X driver crash problem, which was solved by the most recent nvidia release?
[http://www.nvidia.com/object/linux_display_ia32_169.09.html](http://www.nvidia.com/object/linux_display_ia32_169.09.html)

---

### Post by ggreco on 2008-01-23
There is a way to install those new drivers in a clean way so that a kernel update don't break the installation? Some unofficial repository carrying the new drivers in a dpkg and offering them as replacement for nvidia-glx and nvidia-glx-new would be nice :)

---

### Post by Thorning on 2008-01-23
Astalavista>
No, I don't belive so. My nvidia-driver version is 169.09.

---

### Post by RebounD11 on 2008-01-23
Ok then ... your xorg.conf is a rather mess... tons of devices... however, you say that only desktop effects don't work. Well, I will asume that:

```
glxinfo | grep rendering
``` 

returns

```
Direct Rendering: Yes
```

and try to tell you what to do next. Try like this:

Do this in a terminal:
```
nvidia-xconfig --composite
nvidia-xconfig --render-accel
nvidia-xconfig --add-argb-glx-visuals
```

then manually add these lines to your xorg.conf file:

to the ServerLayout section:
```
Option   "aiglx"    "true"
```

to the Extensions section:
```
Option   "Composite"  "Enable"
```

or if there is no Extensions section add tis to the end of the file:
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

save the file and restart X by pressing:

```
Ctrl+Alt+Backspace
```

Hope this works for you :D

---

### Post by Thorning on 2008-01-23
glxinfo | grep rendering did return "Direct Rendering: Yes", yes.

However it didn't change anything noticably, and ... now I'm a bit f-cked :)

(thanks btw Rebound, it was not your tip that f'd things up, it was me)

After trying these settings I didn't notice any differece, however the extra visual effets still asked me to install the glx-new driver, just like before.

(I figgured these setting was meant to have linux use the glx-drivers that came with the nvidia system drivers, instead of having to install the new extra package, or something like that (?) anyhow, the system obviously could not find a replacement or the required drivers   ... it wants that extra installed glx-new-driver)

So I figured since it didn't work anyways to try and install it (nvidia-glx-new) to se if I got the same effect as before ("Fail to query the GLX server vendor").

Done and done, reboot ...

Now the system "locks up" when -Starting manual drivers- ... It's responsive but does not go any further. 
I can come as far as logging in.  By pushing ctrl+alt+del it seems to skip over it and continue (x does not start any more, but reports no problems .. it's not trying to start it). 
I figured I'd try to run "sudo nvidia-xconfig" but it claims to be unable to write to /etc/X11.
ok, wtf (?)
Well, I'll install the system-driver again then.
sudo sh NVIDIA-Linux-x86_64-169.09-pkg2.run
cannot write to /tmp/blabla : file system is read only

.... I'm writing this in windows :( 
I have no idea what to do. I'm sorry for maybe being a bit of a pain in the ***, but this is not something I expected to encounter.

---

### Post by rayman_3d on 2008-01-23
ok , try the envy !! very good for compiling the driver !! i got the same card with no problems !
just install envy , the driver is ready , i did this

compiz --replace

everything is fine now !!

---

### Post by Thorning on 2008-01-23
I'll do that as soon as I get the system running again.

Updates:
I can start the system problem free with x-server by selecting a previous kernel in the boot-list and the disk is then R/W.
Using this, I completely removed nvidia-glx-new and rebooted as normal, but the problem remained.

The system stops after the following, as I see it:

* starting kernel event manager
*loading hardware driver
udevd-event[3747]: run program: '/sbin/modprobe' abnormal exit
*setting system clock
*loading kernel modules...
*loading manual driver... 
... 
... 
... and there's nothing more after this.

*** At this point the system is still responding but I can't see anything on the other tty's.
I then press ctrl+alt+del and it continues with: ***

init:rcS main process (2592) killed by TERM signal
init:rc6 main process (4919) killed by TERM signal

kinitname_to_dev_t(/dev/disk/by-uuid/c3832ccd-45blablabla)=hdb6 (3,70)
kinit: trying to remove from /dev/disk/by-uuid/c3832ccd-45blablabla..
kinit: No resume image, doing normal boot

*loading ACPI modules...
*starting ACPI modules...
acpid: can't open /var/log/acpid: Read-only file system
*starting system log daemon...
chown:changing ownership of /var/log/mail...:  read-only file system
chown:changing ownership of /var/log/...:  read-only file system
chown:changing ownership of /var/log/...:  read-only file system
etc
etc
etc
*starting kernel log daemon [OK]
*starting system message bud dbus [OK]
*starting ... [OK]
*starting ... [OK]

fsck reports no problems.
I have not touched fstab or mtab.

---

