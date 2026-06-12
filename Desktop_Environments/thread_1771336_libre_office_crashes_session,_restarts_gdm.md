---
title: "libre office crashes session, restarts gdm"
date: 2011-05-30
forum: Desktop Environments
---

### Post by santiagozky on 2011-05-30
hello,

I think I have found a bug in libre office, but I would like to confirm it with someone else before submitting a bug report.

The problem happens with a spreadsheet that was given to me (attached). following these steps

-go to sheet named summary
-click on cell C16
-click on the value so the entire formula appears (quite long)
-go to any other sheet
-click on any cell

it restarted my session on my computer, but it didnt happen under a vbox virtual machine. So this could be hardware related

my system:
ubuntu natty, 64 bits.
dell studio 1558
intel i3, integrated gpu
4gb of ram.

---

### Post by rountrey on 2011-06-22
i have a little more serious of a bug, i'm trying to track it down now. i removed openoffice, and installed libreoffice from the ppa. while i waited i started reading some news (with firefox). suddenly, everything started closing (gnome-terminal, firefox, nautilus, and synaptic) then there was nothing. no reply from keyboard or mouse, just a black screen. tried ctrl+alt+f2 and got a terminal, could not run gdm, startx, nothing. figured something went wrong with the install so, sudo reboot it is. it took a little longer to come up but the only thing that came up was the login wallpaper, not the login box. to make it short >>
-ctrl+alt+f2
-apt-get purge libreoffice*
-apt-get autoremove
-reboot
everything comes up just like normal
-log out
-ctrl+alt+f2
-sudo apt-get install libreoffice
some screen cycling (on and off, like x was initiating) at the end of the install but it seemed ok
-reboot
and it gets stuck again.

have you heard anything about this?
the computer is about 5 years old running lucid but new HDD and has an ATI radeon 200 in it. i've heard that there is a bug with libreoffice and ati cards but i cant find any with ubuntu, then again i havent finished looking yet

---

