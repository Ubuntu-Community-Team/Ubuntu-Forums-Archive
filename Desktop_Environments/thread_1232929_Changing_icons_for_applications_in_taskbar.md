---
title: "Changing icons for applications in taskbar"
date: 2009-08-06
forum: Desktop Environments
---

### Post by swinky on 2009-08-06
I am using Firefox 3.5 that I installed manually (from the Firefox website) after completely removing Firefox 3.0 from my system. I have been running it like this just fine pretty much since Firefox 3.5 was released.

Tonight I noticed that the icon for Firefox in the taskbar is the generic application icon. I don't know if that just changed or if I have not been noticing all this time (sadly enough, that may very well be a possibility.) It is the correct Firefox icon in the applications menu, but only because I manually set it. Unfortunately, I don't know how to change the icon for the taskbar. Does anybody know how this would be done?

I've included a picture because for some reason, while I have found a number of posts around the internet asking how to do this, they are always answered with how to change it in the *applications menu*. So the picture is just to reiterate and better illustrate my point.

---

### Post by swinky on 2009-08-06
Um, okay, I that was weird. I solved my own problem.

Apparently, something with ia32-libs got messed up. I realized that more than just the taskbar icon was screwing up after posting... none of the icons would load! So I ran Firefox from the terminal and was getting all sorts of errors like: 
> Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so

Despite trying to install "libpixbufloader-png.so" with getlibs it didn't work. I tracked it down on some forums to an issue with ia32-libs. I uninstalled and reinstalled them, everything is back to normal.

So you can totally disregard this thread... #-o

---

