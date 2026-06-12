---
title: "Can't run commands outside of the terminal like logout, restart and launching video"
date: 2016-03-23
forum: Desktop Environments
---

### Post by amadis2009 on 2016-03-23
I broke something in Ubuntu that is causing problems with launching applications and commands. I can no longer logout or shutdown from anywhere but the terminal. (Actually I've only tried shutdown and reboot from the terminal because I can't figure out what command will log out from the terminal in 15.10.) Also, some of my applications will not launch except from the terminal. Sometimes after a reboot I can get one of them to launch *once*, but if I close the application and try to launch again, then it will not work. The appplications which will not launch are video programs SMplayer2 and VLC, but ***not*** the Ubuntu default video player. That video player launches just fine. Also, the Calibre e-reader program does not launch outside of the terminal. I also cannot open any video files or e-reader files by double-clicking or right click/selecting, with the exception of video files using Ubuntu's default video program.

Prior to noticing these problem, I was having a problem with my keyboard media key/shortcuts not working. While researching that issue I tried the fixes suggested in [this]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1302885") bug report. Neither the Cairo Dock nor the gnome3 solutions worked, and shortly after that I began to notice the problems with logout, shutdown and launching apps. I still can't get media keys to work either. I think the gnome3 solution was probably a really bad idea and I tried to revert that but still the problems persist. Can anyone give me any idea what is causing all of this?

---

### Post by amadis2009 on 2016-03-23
I was able to fix a part of the problem. I opened a terminal from the dock instead of with ctr+alt+T and when I ran SMPlayer2 there I got an ICE error. I deleted the ~/.ICEauthority file and rebooted. A fresh .ICEauthority file was generated and now I can launch SMPlayer2, VLC, and Calibre like normal. But logout, shutdown, and restart still don't work from menus or launchers, only in the terminal.

---

