---
title: "Updated kernel broke fglrx"
date: 2007-04-15
forum: Desktop Environments
---

### Post by Mr. Smiley on 2007-04-15
I updated my kernel to 2.6.20.7 to an Edgy install and now my fglrx drivers for my ati x1400 mobile seem to have broken my 3D acceleration. Typing fglrxinfo gives me:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I tried these commands:
mkdir -p /usr/X11R6/lib/modules/dri 
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri
like it says [Here]("http://wiki.cchtml.com/index.php/Troubleshooting") but it didn't change anything.
I didn't compile the drivers, I used the ones in the repositories.
Any help would be great! If you need any more info please ask.

---

### Post by shae on 2007-04-15
The drivers in the repository are compiled against a specific kernel version.  When you updated your kernel to the newer version, your driver can no longer be loaded into the kernel as a module.  I am shocked you could even boot into X!  I would recommend either going back to the kernel from the repository or to install the latest drivers from AMD/ATI.  

If you have to use a newer kernel and you cannot get the official drivers from ATI to work, then I am not sure what to tell you but that feisty is out soon sporting the newer 2.6.20 kernel and restricted drivers which work.  

For help installing the ati drivers, consider:
[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

and 

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

