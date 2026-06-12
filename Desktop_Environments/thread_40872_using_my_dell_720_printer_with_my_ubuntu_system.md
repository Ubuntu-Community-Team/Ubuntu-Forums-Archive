---
title: "using my dell 720 printer with my ubuntu system"
date: 2005-06-10
forum: Desktop Environments
---

### Post by aeromaverick on 2005-06-10
hi guys

i got a free dell 720 color printer with my laptop. i was tryin to configure this with my ubuntu linux system. can ne body tell me how i can do it. there areonly 2 drivers for the del printers. i tried both. i tried takin a text print. but nothin happens

thanks

aeromaverick

---

### Post by joneall on 2005-10-27
I see 3 open threads on this subject.  There is a closed thread at

[http://www.ubuntuforums.org/showthread.php?t=56631&highlight=dell+720](http://www.ubuntuforums.org/showthread.php?t=56631&highlight=dell+720)

which gives a howto.  When I tried it, tho, I got

# sudo dpkg -i z600cups_1.0-2_all.deb
Selecting previously deselected package z600cups.
(Reading database ... 76537 files and directories currently installed.)
Unpacking z600cups (from z600cups_1.0-2_all.deb) ...
dpkg: dependency problems prevent configuration of z600cups:
 z600cups depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.


When I tried to apt-get libstdc++5, it wasn't found.  Does this mean I need to turn on the universe repository in /etc/apt/source.list?

What danger is there in turning on universe?

Thanks in advance.  John

---

