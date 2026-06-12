---
title: "X Restarting On Login"
date: 2010-04-11
forum: Desktop Environments
---

### Post by lapgoat on 2010-04-11
I was using my computer normally when I accidentally knocked the USB cable out of my PSP, which was mounted and transferring data.  When I plugged the USB cable back in, my system froze.  I powered it off and then back on and when I went to log in, I found that each login attempt X would show a black screen for maybe a quarter of a second and then return to the login screen as if X had completely restarted.

Logging in via command line, I did:
```
daniel@Desktop-Ubuntu:~$ dmesg | tail
...
unrelated stuff
...
[   27.166442] type=1503 audit(1270961561.057:32): operation="open" pid=2285 parent=1665 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/daniel/.profile"
```(I have no wireless access without logging into gnome, so I had to type this all out by hand.  I don't see any typos in it, but that doesn't mean that I didn't miss any.)

I tried creating a new user and logging in with that and got the same error in dmesg (uid, username, pid, and parent changing as applicable, but same file in the user home).

Does anyone have a clue what I can do to get back into gnome?

Notes:
I'm running Karmic
Running NVidia 185 driver from the repos
Haven't touched X or NVidia settings since I got them working the day I installed Karmic

---

