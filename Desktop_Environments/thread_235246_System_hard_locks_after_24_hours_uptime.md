---
title: "System hard locks after 24 hours uptime"
date: 2006-08-12
forum: Desktop Environments
---

### Post by evillawngnome on 2006-08-12
Alright, ive got a number of ubuntu systems and this is the only one that gives me grief. Here are the stats:

CPU: AMD XP 3000+ (32-bit)
RAM: 512 MB
HD1: IDE 40GB
HD2: SATA 120GB

Ubuntu boots off of HD1. Ive got a few extra things running, this isnt a vanilla install. Ive got a vnc server and SSH server, and thats it. Seems like after a day or so, the system hard locks in some way. 

Hard lock style one:
Im never logged in locally, so i try to log in remotely and get connection refused or some such when it normally works. I try to log in locally to diagnose the problem. I put in my username and it doesnt jump to password field, it just stays grayed out. I cant switch to another TTY, nor can i move the mouse.

Hard lock style two:
Same as above, except when i try to login locally, it says something like "spawning too fast, disabling for 5 minutes". I can switch to another tty, but i get the same problem.

**My question:**
WHich log files to i need to be looking at, what can i be looking for to pin down where things are going wrong?

---

### Post by evillawngnome on 2006-08-12
Update: Ive gone from using the 386 kernel to using the k7 kernel; we'll see if this helps.

---

### Post by evillawngnome on 2006-08-12
Update: Using the k7 kernel does nto help; in fact uptime was reduced to about 3 hours this boot. I was logged in remotely(over lan) via vnc and it locked up. I had to kill the VNC process on the remote machine. When i came in, the keyboard/video was unresponsive. **Does anyone have any ideas on what can be causing my machine tolock up requiring cold reboot?**

---

### Post by taurus on 2006-08-13
Not sure exactly why because my machine was up for 45 days one time until the power outage took it down.  Do you happen to mount any network drives from your machine?  See if it still locks up without vnc server running!

---

### Post by evillawngnome on 2006-08-13
I might give that a shot, but i think rather than a hard crash, i think vncviewer would just die. I used to have this same problem with 5.10, so im wondering if its my asus v7700 video card. It worked out of the box, but its a really old card, so i might try another video card if i can find one.

**Im still wondering if there are log files i could be looking at...**

---

