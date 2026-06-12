---
title: "[SOLVED] upgrade caused problem"
date: 2008-09-14
forum: Desktop Environments
---

### Post by The Shadow on 2008-09-14
I was running Ubuntu Kernel 2.6.17-10 with no problems. I upgraded to Kernel 2.6.17-12 and my system would no longer boot. After the login screen I would simply get a blank screen.

I have not been using linux for a while so i just left it alone. Today I tried to boot my system and had the same problem but was able to get in using the "failsafe gnome".

The system would not allow me to update, it kept asking for an "Administrative Password". so I went into single user mode and set a new admin password. Now I get "E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct problem. I did, but the operation did not complete. I hung up at 

"invoke -rc.d:initscript dbus, actio "force -reload" failed"
*starting Hardware  abstration layer hald

it did however update my kernel to 2.6.20-16

I downloaded the latest Ubunto (8.02?) and put the image on a live disk. it runs fine, but without support for my bluetooth mouse and keyboard.

anyone have any suggestions?

---

