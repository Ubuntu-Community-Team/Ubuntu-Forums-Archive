---
title: "CS Source Issues in Kubuntu"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by scribbles on 2007-08-27
I'm running Kubuntu and have gotten Steam to open and download games fine. The issue I'm having occurs when I dbl click on CS Source, I close the Steam window per many guides instructions. The window opens and I see the CS logo and it says Loading just like normal. Then the screen either goes black and nothing happens or after the resolution changes I see my desktop zoomed in and I have to restart kde to get past it. Anyone run into this before? Attached is the output from Konsole I copied....

---

### Post by scribbles on 2007-08-28
So it was recommened to me in #winehq that I reinstall wine because of the usage of sudo. I've done that and it's back up and running again, same issue with CS, when I open CS the resolution changes I see the loading screen then I'm back to the desktop with an altered res.

I also followed the Ubuntu docs install for fglrx  and now when I start Steam I get:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

which I never got previously...

---

### Post by Hyperkill on 2007-08-28
Try loading the restricted drivers manager in kubuntu by typing sudo /usr/bin/restricted-manager

Check the box and reboot and see if the problem is solved.

---

