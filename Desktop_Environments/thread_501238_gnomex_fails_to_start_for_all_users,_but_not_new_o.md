---
title: "gnome/x fails to start for all users, but not new ones (ubuntu-studio)"
date: 2007-07-15
forum: Desktop Environments
---

### Post by cargobidibulle on 2007-07-15
Hello 

here is a bug that has wasted my last weeks and is amongst the worst i have ever seen.  Any help would be greatly appreciated. I am still relatively new to linux.

I installed ubuntu studio and it works ok after installation for several days in a row. (I reinstalled it 4 times already) However, every several days (irregular), some configuration is lost after shut down. Next boot I can go up to inputing login and password. but after that, i only have a black screen with the white pointer moving freely over it.

The computer does not actually freeze:
ctr/atl/backscape brings me back to login windows
ctr/alt/F1 brings me to console mode 

I can access to any user account in console mode, but any attempt at starting the destop (startx command) brings me to a white screen.

I of course tried many things without success. What is most surprising to me is:
- all users existing at the moment of the bug are affected the same way (which would rather indicate a system problem common to all users like xorg settings)
_However, i can create new users from console mode (using useradd) and those can access to gnome without problem (which would rather indicate a user-specific problem)

my conf:
AMD Athlon X2 dual core processor BE-2300 1.9GHz
motherboard ASUS M2A-VM (integrated ATI video)
2 Go ram
OS: ubuntu studio (gnome desktop)

please help me

---

### Post by Alchemista1979 on 2007-07-15
Yup, got the same issue

Installed yesterday all the updates after a week of holiday.   PC continued working fine for the rest of the day.

This morning, I launched the Pc and after logging into GNOME, I get a white screen with my mouse pointer.  Nothing happens after that (not even when I leave it that way for some time)

Euhm, help?

Btw; I did try to recopy a backup version of my xorg.conf (but NOK).  The latest updates were for OpenOffice, so I tried to completely removed them (succeeded), but the problem isn't solved.

Thanks for checking this!

---

### Post by cargobidibulle on 2007-07-15
Alchemista, it may be that you are a lucky person. Let me say that you deserve some popcorn :popcorn:

After one month of wasting all my weekends on that bug, it seems i have found a way out a few hour after posting for help. :)

I typed in a terminal

sudo dpkg-reconfigure -a

this takes through a long reconfiguration process for all the system (allow 1 hour). just enter ok when you don't know.

After that i rebooted, and everything was back to normal.

It is sort of a heavy cure but it worked.

---

### Post by cargobidibulle on 2007-07-22
sorry I must say that my cure above worked only once, and the problem came back. :(

I have to conclude that ubuntu studio is too unstable today. (too bad because apart for that, ubuntu studio was great.)

I gave up, and came back to the main stream ubuntu 7.04

---

