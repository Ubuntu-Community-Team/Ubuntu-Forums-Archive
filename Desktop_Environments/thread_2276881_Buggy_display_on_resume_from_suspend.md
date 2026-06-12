---
title: "Buggy display on resume from suspend"
date: 2015-05-05
forum: Desktop Environments
---

### Post by David_Abergel on 2015-05-05
Hi all,

I'm using xubuntu 15.04 (so I presume that's xfce-4.10), and I am having some problems when my laptop resumes from a suspend. I think that it's a problem with X, rather than a hardware issue, but I don't really know where to start with diagnosing the exact issue.

The symptom is that, on resume from suspend, the display does not update properly. Icons are missing, text is absent from program windows, desktop icons are not there. If I move the mouse over a window or the place where an icon should be, sometimes it will be redrawn, and sometimes not.

I have done a bunch of googling, and read a lot about light locker issues on resuming. I don't think this is the problem, because if I enable light locker and as it to lock on suspend, the laptop resumes properly, and the same symptoms on the display are present on the light locker password screen.

So, any ideas what this could be?

Thanks!

---

### Post by David_Abergel on 2015-05-05
Sorry, I made a mistake in my initial post. Running xfce-about tells me that I in fact have xfce-4.12. Apologies.

---

### Post by David_Abergel on 2015-05-08
After further investigation, I have found a number of potentially helpful things.

1. If I restart the window manager with 
xfwm4 --replace --daemon 
after I resume, then the problems seem to decrease significantly. The windows, desktop icons, and panel icons redraw themselves. The only issue I can see is that text in popups when you mouse-over things is still a bit wrong (systematically, bold face letters 'm' and 'c' seem to not be displayed, for example). I have been trying to put this command into a script which will run when systemd resumes the machine, but I cannot work out how to do this. (I think 15.04 uses systemd rather than pm-utils to manage suspending when the laptop lid is closed, but please correct me if I am wrong.)

2. If I run a program with hardware acceleration (such as google chrome) after resume, this seems to help a little. I still have to mouse over all the icons etc once to make them redraw, but when they do, they stay properly drawn.

This makes me wonder if the problem is in xfwm4, or somewhere in the video driver. Any thoughts?

Thanks.

---

### Post by David_Abergel on 2015-05-17
Some more info, in case anyone else is struggling with similar issues.

The more I investigate this, the more likely I think it is that there is a driver issue, either in the kernel or in X. However, I am still currently unable to get the laptop to reliably resume from suspend without the graphical bugs that I referred to above. The two tweaks in post #3 sometimes (but not always) help.

---

