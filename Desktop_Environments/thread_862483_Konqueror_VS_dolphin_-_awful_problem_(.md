---
title: "Konqueror VS dolphin - awful problem :("
date: 2008-07-17
forum: Desktop Environments
---

### Post by IFailAtLinux on 2008-07-17
I had a folder on my desktop. When I clicked on it it opened with Dolphin, which I find pretty bad. I wanted to get it with Konqueror so I right-clicked on the folder, choose "Open With -> Konqueror" and remember the action. The folder opened with Konqueror.

And here problem starts! Now whenever I click on a folder on desktop it opens with Konqueror BUT then clicking on any folder inside conqueror window will open in Dolphin window! And no matter how I start the konqueror. I can't use my conqueror normally at all :< How do I fix it?

---

### Post by pluviosity on 2008-07-17
Try following the instructions at this website and see if it helps:  [_link_]("http://www.microswamp.com/tech-notes/linux/38-linux/61-replace-dolphin-with-konqueror-in-kubuntu?345342a77c2a05fb40d72306ce9fe915=faeb28942607aa9280ff590f2de0917d")

---

### Post by IFailAtLinux on 2008-07-17
Thanks a lot :) Actually following things in that tutorial didn't work, the settings in kcontrol run as root were different than when run as normal user. I didn't want to completely delete Dolphin but when I ran it as myself and changed stuff the same way the things work like they should!

---

### Post by stitchmysmile93 on 2008-07-18
I noticed that when you right click open with other w/e program it is it will continue to open that kind of file in that program til you change it...

---

### Post by red_team316 on 2008-07-18
Go under Settings...KDE Components...File Associations. Once there go to inodes, and then find folders, it should let you set what app takes priority, set konqueror above dolphin.

---

