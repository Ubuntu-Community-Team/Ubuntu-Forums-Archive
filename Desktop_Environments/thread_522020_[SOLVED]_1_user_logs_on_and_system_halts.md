---
title: "[SOLVED] 1 user logs on and system halts"
date: 2007-08-10
forum: Desktop Environments
---

### Post by TravMan63 on 2007-08-10
I have 3 users on system (1 is root)

root and user 1 can log into x - ok

if user 2 logs into x - it often halts the system (within a minute) - sometimes if I continue moving the mouse, X will exit.... back to gdm

control alt backspace, and control alt f1 - .... does nothing - if connected via ssh - it goes down -it is DEAD (power is still up - the panels (gnome) are garbled...

I had installed wicd, but seemed to have some connection (seemed quite a bit slower) problems (I don't think it would 'behave' differently with tinyproxy, dansguardian and firehol...) , removed wicd - put network-monitor-gnome and network-monitor both back on... (and off and on - purging as well - still halts) -- but believe I have narrowed it down to this user  --- what can I check?

Thanks
TM

btw - if wicd works for you - it does connect much better with other wireless networks - something I couldn't get network-manager to do

--edit 1
logging on with 'failsafe gnome' - n/c
I renamed the folder /home/user/nautilus - n/c (no change - same results - still halts)

-- edit 2
user 1 changed screen resolution - and now they halt (user 2 is 1st account created)

nvidia 4 go 440 32 MB

resolution for user 1 and root are the same, yet root never crashes .... yet

------------------
SOLVED - mostly 

I placed all the folders in the users home directory (except for desktop and maybe a few others) - into another folder.
There must be some config problem - but which file?  Dunno.

Doing this also changed menu configuration etc.../placement...

---

