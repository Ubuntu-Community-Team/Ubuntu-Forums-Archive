---
title: "xine/totem cause gdm restart"
date: 2005-09-19
forum: Desktop Environments
---

### Post by trash on 2005-09-19
installed from the backports on a compaq presario v2000.
At first i thought it was a dvd issue but now realize that even without a dvd starting these apps just causes X to exit and brings me back to the login.
I can't find any logs that tell me anything useful or posts with this problem... anybody experienced this?

can anybod say if this machine is a good candidate for Breezy... i'm already tempted!

---

### Post by trash on 2005-09-20
getting somewhere... this worked.


Error Messages: What they mean and what you can do
Starting xine crashes XFree, I am logged out of my desktop!

xine itself is unable to crash XFree, so when your X server just shuts down or restarts with the login screen, there is something wrong with your X setup. Most common are problems with the Xv extension. Try running xine with the XShm video output plugin: 

   xine -V XShm

If that works fine, you just proved, that the Xv extension is buggy. xine will remember the last used video output plugin, so the setting will stay at XShm. You could simply continue using this, but XShm is a lot slower than Xv, so consult the section on Xv and see if you can get it working. Usually you should look for updated versions of the XFree driver module that belongs to your graphics card.

---

### Post by akvik on 2005-12-09
Hi, I have the same problem - when my second monitor (TV) is not connected, gdm crash when using xv watching video. Have someone been able to find the solution yet?

:-)

---

