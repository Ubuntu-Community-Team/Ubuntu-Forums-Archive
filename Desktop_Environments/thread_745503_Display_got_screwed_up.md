---
title: "Display got screwed up"
date: 2008-04-04
forum: Desktop Environments
---

### Post by smithbp1 on 2008-04-04
I just installed Ubuntu on my computer, and it is pretty much my first time using any form of linux, so any solutions to my problem need to be explained very simply and clearly. My screen was not centering right, so I went into the the system-->administration-->screens and graphics and I changed the screen to Sony SDM - HS73. When I logged out to make the settings stick, the screen became completely unreadable. Is there some way to undo what I did? I can't read the GUI at all, and I don't really know any commands to do it in the recovery console.

Any help would be much appreciated. Thanks

---

### Post by overdrank on 2008-04-04
> **smithbp1 said:**
> I just installed Ubuntu on my computer, and it is pretty much my first time using any form of linux, so any solutions to my problem need to be explained very simply and clearly. My screen was not centering right, so I went into the the system-->administration-->screens and graphics and I changed the screen to Sony SDM - HS73. When I logged out to make the settings stick, the screen became completely unreadable. Is there some way to undo what I did? I can't read the GUI at all, and I don't really know any commands to do it in the recovery console.

Any help would be much appreciated. Thanks

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

