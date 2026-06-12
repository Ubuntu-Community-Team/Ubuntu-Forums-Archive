---
title: "New User and Samba"
date: 2005-11-25
forum: Desktop Environments
---

### Post by black_wolf on 2005-11-25
Hello,

Right now I'm dual booting my computer with XP and Ubuntu. I've tried other distros but I found Ubuntu to have the nicest interface and the easiest to configure (mostly) with great forums.

I'd like to network my other Windows boxes so that I can share folders and a printer, I have one running XP and another running 98.

I've searched the forums, google, and just about everything else attempting to find a Samba tutorial that worked for me. So far I have installed Samba and swat using apt-get, but I've had trouble configuring it to work correctly.

Once installing samba, I attempted to configure it by editing smb.conf with my workgroup info and poked around with a few of the settings. I attempted to set up SWAT although one of the steps in the tutorial that I was following had me kill the inetd process after uncommenting the start swat line in the inetd.conf file. I run the ps ax command from the term but I can't find the process.

Making a new post on the forums about samba was the last thing that I wanted to do because I search and google and attempt to figure this out on my own, but I'm a linux newbie, and I think I might be in over my head. Help is greatly appreciated. :D

---

### Post by manicka on 2005-11-25
This how-to has never let me down for file sharing

[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

---

### Post by black_wolf on 2005-11-25
Even if I've already tried configuring it once, should I start from scratch this time?

Therefore I should start with apt-get and continue from there?

---

### Post by heart_reaver on 2005-11-25
No harm in it. But do note this :**when taking backup , may be orignal configuration backup file will be overwrite in modifing then ** Make your eyes open will using ubuntuguide

---

