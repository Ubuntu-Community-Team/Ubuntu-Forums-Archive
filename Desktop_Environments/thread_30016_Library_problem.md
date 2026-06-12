---
title: "Library problem"
date: 2005-04-26
forum: Desktop Environments
---

### Post by audaz on 2005-04-26
I am trying to use synaptic to get some new apps. One of the necessary files needed for these apps is the libSDL_image-1.2 file. I get this error message when I try to apply it to my system:

E: /var/cache/apt/archives/libsdl-image1.2_1.2.3-6_i386.deb: trying to overwrite `/usr/lib/libSDL_image-1.2.so.0', which is also in package sdl-image

I have tried this several times, and even erased the libSDL_image-1.2.so.0 from my /usr/lib directory, but apparently, the installer puts that file there and then tries to overwrite it?.......

Is that file broken, and should I just give up? This is driving me nuts (not as nuts as my ATI card mind you). ](*,)

---

### Post by panzer77 on 2005-04-26
I ran into the same problem when I did an update today.  Go to System>Administration and launch synaptic package manager.  At this point my system reported a broken package.  You can filter for the broken package or click on custom in the bottom left corner.  At this point I selected to Mark for Removal, it in turn will also uninstall several other files.  I'm running Gnome and everything seems to be OK after I did the removal.  It appears to be related to KDE or KDE lib/apps?

---

### Post by audaz on 2005-04-26
Thanks for the reply. I have uninstalled it and i don't get the error message anymore, but there are several apps that rely on that library (mostly games). 

I guess we'll just have to wait until someone gets that lib fixed for gnome.

---

