---
title: "Xfce DE failing to load in X/ubuntu 9.10"
date: 2010-01-27
forum: Desktop Environments
---

### Post by auburnfan2015 on 2010-01-27
Thought you guys might have some more suggestions for my problem:

 I did a fresh install of Ubuntu Karmic on my Dell Mini 9, got it up and running, and installed Xubuntu through "sudo apt-get install xubuntu-desktop". I rebooted, logged into Xubuntu, and everything ran smoothly. When I left the room, I powered down my Mini 9 properly and plugged it in to charge. Just now, I tried several times to log into an Xfce session like normal, but when I put in my password, my Xubuntu background and a cursor appears and nothing else. I can't do anything with the cursor but move it, but I can open terminal with ctrl-alt-F1. I powered down and logged into a GNOME session, and it worked perfectly. Ubuntu's up and running with no problems. Can anyone explain why the Xubuntu environment is not loading? 

Thanks in advance for the help!

---

### Post by auburnfan2015 on 2010-01-28
bump.  anyone have an idea, a starting point at least?

---

### Post by themtx on 2010-01-28
Don't know why xfce hung on you like that, but I'd log into a terminal session as root, rename current /home/username to /home/username_OLD, then mkdir /home/username, then lastly chown username:username /home/username

You should then be able to log in to xfce again as username and get a nice default desktop.

---

### Post by nowell29 on 2010-02-02
I love XFCE, but sometimes, for reasons I do not understand, my panels don't come up.  alt-F2 will bring up the run dialog, and type in: xfce4-panel

See if that doesn't bring things back to norm.  Like I say I have had to do that, but it is not that often.  I tend to customize my setup so much that I wonder if I occasionally break it.  (like now!)

---

