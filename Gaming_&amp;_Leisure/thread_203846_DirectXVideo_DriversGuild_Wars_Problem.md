---
title: "DirectX/Video Drivers/Guild Wars Problem"
date: 2006-06-26
forum: Gaming &amp; Leisure
---

### Post by xenex on 2006-06-26
[img]http://img20.imageshack.us/img20/6320/guildwars9um.png[/img]
My video card is nVidia Corporation NV11GL [Quadro2 MXR/EX/Go] according to Ubuntu. I have nvidia-glx installed.

NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one.

To enable the driver, run "sudo nvidia-glx-config enable".

I typed "sudo nvidia-glx-config enable" and I got this.

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

Any ideas?

---

### Post by Perfect Storm on 2006-06-26
Check your xorg.conf if the card driver is set correctly.

---

### Post by xenex on 2006-06-26
Okay I changed nv to nvidia but I get the same error from Guild Wars. Would a restart be required after the .conf change?

---

### Post by Perfect Storm on 2006-06-26
Yep.

---

### Post by xenex on 2006-06-26
Yeah...that messed up my X. It won't start. I'm currently on a LiveCD. Mind telling me how to restore it?

---

### Post by Perfect Storm on 2006-06-26
sudo nano /etc/X11/xorg.conf

change back to nv

---

### Post by xenex on 2006-06-26
Uh it's already set to nv again.

---

### Post by Perfect Storm on 2006-06-26
and you can't still log into X?

Edit: you have to do it in failsafe of your installed ubuntu.

---

### Post by xenex on 2006-06-26
I think you made me edit the xorg.conf on the LiveCD. But I'll restart right now to see.

---

### Post by xenex on 2006-06-26
Yeah, it didn't work.

---

### Post by xenex on 2006-06-26
What is failsafe?

---

### Post by xenex on 2006-06-26
Nevermind I got xorg back. Now, how do I get Guild Wars to work? :\

---

