---
title: "Unattended system slows to a crawl"
date: 2006-07-30
forum: Desktop Environments
---

### Post by MrNiceguy on 2006-07-30
I have a problem where, if I leave my system for a couple of hours and return, the system is unusably slow.  I tried disabling the power management settings, but that didn't help.

I fully admit to being a linux newbie, but I have tried to figure the problem out on my own.  I don't think the problem is caused by the screen saver, because if I'm only gone for 30 min or so, everything recovers fine and is perfectly usable.

When the system is crawling, I can switch to one of the command line sessions, but it takes probably 30-45 seconds between when I press ctrl-alt-Fwhatever.  Logging in at the command line is very slow as well - about 3-5 min between typing in the password and having a prompt.  I ran 'top' and sorted by cpu usage, but it showed cpu usage in the single-digits with the xorg as the highest process - about 5%

System specs - P4 2.8 Ghz, 1GB RAM, 200 GB HDD with ubuntu using 40 GB for / and 2 GB swap, Radeon 9600 video card

I'm using the fglx drivers and I've heard there can be some stability issues with them.  Is that what I'm running into here?  Or does anyone else have any suggestion for things I can check?  I appreciate the help.

---

