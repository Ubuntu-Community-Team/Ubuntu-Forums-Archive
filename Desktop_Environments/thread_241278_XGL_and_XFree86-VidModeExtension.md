---
title: "XGL and XFree86-VidModeExtension"
date: 2006-08-22
forum: Desktop Environments
---

### Post by sarikan on 2006-08-22
Hi there, 
I am trying to use vmware under xgl, and my problem is: when the guest os (xp ) is started, It just displays an empty black part. 
The problem exists with xgl, since xorg has on problem with it, and under xorg full screen also works. 
Under xgl, I think there is an overlay problem. I had issues with remote desktop, but exporting XLIB_SKIP_ARGB_VISUALS=1 fixed it. However, it had no effect on vmware. I have noticed that when I use vmware, the following is printed on the terminal: lib:  extension "XFree86-VidModeExtension" missing on display ":1.0". 
Also vmware complains about not finding the appropriate host resolution in host, which is not a problem under xorg. 
So, no overlay, no fullscreen, and vmware is pretty useless under xgl. (well, I have managed to use terminal services client, but it's not a performance wise solution) This is drake with nvidia drivers and 6600 go on a packard bell laptop

Best Regards

---

