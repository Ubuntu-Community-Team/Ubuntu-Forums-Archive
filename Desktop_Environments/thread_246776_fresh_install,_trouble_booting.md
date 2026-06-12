---
title: "fresh install, trouble booting"
date: 2006-08-29
forum: Desktop Environments
---

### Post by illfilles on 2006-08-29
i have been trying to get up and running with version 6.06.1 and i'm having a bit of trouble. installer runs through just fine. seems to be partitioning all right with 2.9 gb for swap, aproximately 300 mb for /boot, and the rest split in half for / and /home.

after ejecting install cd and rebooting i can only get this far:


* Configuring network interfaces....                             [ok]
* Setting up general console font...                             [ok]
* Setting up per-VC fonts...                                     [ok]
* /dev/tty2                                                      [ok]
* /dev/tty3                                                      [ok]
* /dev/tty4                                                      [ok]
* /dev/tty5                                                      [ok]
* /dev/tty6                                                      [ok]

* INIT: Entering runlevel: 2                                     [ok]
* Starting system log...                                         [ok]
* Starting kernel log...                                         [ok]
* Starting RAID monitoring services...                           [ok]
* Starting deferred execution scheduler...                       [ok]
* Starting periodic command scheduler...                         [ok]
* Running local boot scripts (/etc/rd.local)                     [ok]

Ubuntu 6.06.1 LTS ubuntu tty1

ubuntu login:

at this point i can log in and use the command line but i can not figure out a way to get to the GUI.

can someone help me figure out what is wrong here?

thank you.

---

### Post by Omnios on 2006-08-29
Are you shure you did the desktop install, there is also a server install that leaves you with a command line.

---

### Post by missmoondog on 2006-08-29
try typing startx

i just did a fresh install of ubuntu also and get to that same last line (Running local boot scripts (/etc/rd.local) [ok] and it just sets there. i can type startx and get to the desktop. not everything is working correctly though. terminal will not load is what i've noticed so far.

what is this "Running local boot scripts (/etc/rd.local) [ok]" at the end? never seen that beofre.

thanks

---

### Post by illfilles on 2006-08-29
not sure what "Running local boot scripts (/etc/rd.local) [ok]" is yet, but i did realize that i was trying to install from the server install image. currently downloading the desktop image to install from that.

---

### Post by missmoondog on 2006-08-29
i'm almost next to positive i didn't install the server version. about to attempt kubuntu again.

here's hoping!!

---

### Post by mssever on 2006-08-29
If you nave Internet access, doing [FONT=Courier New][COLOR=SeaGreen]sudo apt-get install ubuntu-desktop[/COLOR][/FONT] (or kubuntu-desktop) should get you what you need without re-installing.

---

### Post by missmoondog on 2006-08-30
yay!! dapper kubuntu is fully functionally installed. booted computer up with windows 98 boot disk and did an fdisk and scandisk before trying this last install. whether that fixed it or not doesn't matter, but i had remembered that i read about doing that somewhere before.

back to being a happy camper again! :)

---

