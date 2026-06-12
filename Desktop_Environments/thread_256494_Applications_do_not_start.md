---
title: "Applications do not start"
date: 2006-09-13
forum: Desktop Environments
---

### Post by cryptonite on 2006-09-13
Hi,
I just installed Ubuntu yesterday and really like it. The only problem is that if I try to start some of the Administrative Tools, e.g. "Software Properties", I get a "Starting Administrative Application" bar at the bottom, but nothing opens up. Same goes for the update app and other tools from the "System" menu!
Hope someone can help me out. Thanks!

---

### Post by ayoli on 2006-09-13
this is a bit weird, you should be prompted for your user password in a little window, didn't you see it ?
however, you can try another way by type in a terminal:
```
sudo synaptic
```
then enter your user password at prompt, that should work.

---

### Post by cryptonite on 2006-09-13
Well, I have to log in when I start my computer up, I have to enter my user name and password.

Edit: At the terminal, I get this:
 sudo: unable to lookup  via gethostbyname()

---

### Post by ayoli on 2006-09-13
restart in **recovery mode** (maybe you have to hit ESC at boot to see grub menu), and edit these two files using nano:
```
/etc/hosts 
```
and 
```
/etc/hostname
```
they must have the same name (this is your computer's name).

then save/quit nano with **CTRL+X** and **y**

then reboot in normal mode and try sudo again, i it works try admin apps via main menu.

---

### Post by cryptonite on 2006-09-13
I managed to open up these files with nano, and they both have the same name, except that /etc/hosts contains the additional line "127.0.0.1 -localhost". When I try sudo I still get the same message.

---

### Post by ayoli on 2006-09-13
/etc/hostname contains only compter's name on first line (ie: *zone* in my case)
/etc/hosts should have first line like this:
```
127.0.0.1 localhost zone
```
replace *zone* with your computer name you have entered in /etc/hostname

---

### Post by cryptonite on 2006-09-13
Changed it, but sudo still gives me the same message!

---

### Post by fragos on 2006-09-19
Thanks ayoli -- I just came up with the same problem and as you said it was the hosts file not having hostname in it.  Nano wouldn't let me edit hosts so I did sudo nano to a new file and overwrote the old hosts.  All is well again but now I have to figure out how the hosts file got changed.

---

