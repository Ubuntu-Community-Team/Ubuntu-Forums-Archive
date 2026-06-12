---
title: "3D Screensaver Crash"
date: 2007-01-16
forum: Desktop Environments
---

### Post by treasonx on 2007-01-16
Recently whenever my screensaver tries to come on it crashes the Xserver and the server will restart at the login screen. I tried to go into the screensaver control panel but the preview there will also crash the server and bring me to the login screen. What configuration file contains the config for the screensaver? I would like to go into the config file and just turn off all screensavers or maybe set it to blank screen.

---

### Post by peabody on 2007-01-16
I think it's a setting that can be edited with gconf, but I don't know the specific area in question.  What video card do you have?  My video card would always crash on OpenGL stuff until I installed the ATI official drivers (radeon 9000).

---

### Post by treasonx on 2007-01-16
I have an nvidia card with the nvidia drivers. It was working without a problem up until about a week ago then all of a sudden it crashes.

---

### Post by peabody on 2007-01-16
Have you checked to make sure the nVidia drivers are at the latest version?

---

### Post by jornahow on 2007-01-24
I had the same problem, now solved.  It relates to xgl and I believe a recent update that messed up the nvidia drivers.  In my case because I was running beryl I couldn't get past the login screen - each time I logged in something (beryl?) loaded that kicked me back to the login again.  I removed beryl after logging in as root via recovery mode.  This allowed me to login normally, but every time I accessed the screen saver or anything else that used xgl I crashed to the login again.  I had earlier tried reinstalling the nvidia beta 9742 driver that I had been using - this did not help.  Following some advice on another thread I then installed the nvidia 9762 driver from the nvidia site using their simple guide (you must not be in X when you do this from a terminal).  Now all is well, actually better than before.  Screensavers work and I installed the latest Beryl from the repositories using synaptic and it works flawlessly.  Hope this helps.

jornahow

---

