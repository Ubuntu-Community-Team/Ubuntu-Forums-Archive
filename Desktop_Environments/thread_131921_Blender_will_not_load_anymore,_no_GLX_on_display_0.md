---
title: "Blender will not load anymore, no GLX on display 0;0"
date: 2006-02-17
forum: Desktop Environments
---

### Post by JanvL on 2006-02-17
Hi all,

I had blender working then installed a few other apps and now i get the following note when trying to start blender.
---------------------
jan@ubuntu1:~$ blender -w
Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window
jan@ubuntu1:~$
-----------------------

What to do to get GLX on the display again?

Please give me a hint

Jan

---

### Post by zxee on 2006-02-17
I think the simplest 1st step would be to try an re-install your video driver. It might be helpful to know what was recently installed. Something is either interferring with or has disabled your glx module. Hope that helps.

---

### Post by JanvL on 2006-02-17
Thanks,

It must have been automatix,
this give OpenOffice to 2.0 and Firefox to 1.5.
It did work fine, all the rest is still functional.

Where do I find the videodriver?
Had problems with that on a suse 9.0 and matrox with KDE but
Debian-based systems are a little different, so is Gnome.

What is the config file for X now?

Thanks for the help.

Jan

---

### Post by zxee on 2006-02-20
I was without power for a couple of days so didn't check here. xorg.conf is in /etc/X11. You can also do 'sudo dpkg -reconfigure xserver -xorg' from the commandline to reconfigure x. Hope you get it working.

---

### Post by durand on 2006-02-25
I had the exact same problem as you and i found that nvidia-glx seemed to cause the problem for me. I just had to uninstall it via apt:
```
sudo apt-get remove nvidia-glx
```
The annoying thing is that it means i can't use the official driver:mad:

---

### Post by JanvL on 2006-02-28
Thank you,

removing NVidia glx did the trick, I do not miss the driver so for me its no problem.
Blender is working again so I can try it on Linux instead of win98.

Jan

---

