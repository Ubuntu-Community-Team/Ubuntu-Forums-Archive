---
title: "Unable to install wow (world of warcraft) on ubuntu with cedega"
date: 2005-02-18
forum: Gaming &amp; Leisure
---

### Post by groland on 2005-02-18
the ubuntu forum doesn't like very long code
that's why you have to see my code on another website
[http://transgaming.org/forum/viewtopic.php?t=2039](http://transgaming.org/forum/viewtopic.php?t=2039)


can you help to install this game?

i've read this message
[http://transgaming.org/forum/viewtopic.php?t=1760](http://transgaming.org/forum/viewtopic.php?t=1760)
very similar from my problem but i'm not under fedora

---

### Post by Perfect Storm on 2005-02-18
Do you use the CVS version or the paid version? There's some important Dll files in the paid version which the CVS version doesn't offer. That could be the problem.

---

### Post by groland on 2005-02-19
i've got the paid version
(the Debian Package in fact)

the last version of cedega (4.2.1)

---

### Post by piedamaro on 2005-02-19
Dunno if it will solve your problem, however for cedega I had to put this in /etc/sysctl.conf:
vm.legacy_va_layout = 1

There are other options, it's all in the cedega README.

---

### Post by groland on 2005-02-19
i try to put that in the file (vm.legacy_va_layout = 1)
it doesn't work

---

### Post by groland on 2005-02-21
up

---

### Post by Perfect Storm on 2005-02-21
Perhaps?: [http://mandrakeusers.org/index.php?showtopic=22572](http://mandrakeusers.org/index.php?showtopic=22572)

---

### Post by groland on 2005-02-27
thanks all for your help

now, it's work
i've installed the game on a pc under windows xp
then copy all files on my extern hdd (my iPod in fact, thanks apple)
i've copied them on my pc under linux
and now i can play

bye

---

### Post by rcbaxter on 2005-04-16
How I got it working:

First, some hardware specs for background purposes.  I'm running Ubuntu Hoary 5.04 on a P4 2.8, Abit DuraMAX AA8 motherboard, 512 DDR2 RAM, with an Nvidia GeForce 6600 PCI Express video card.  I had previously installed nvidia-glx using Synaptic.

1.  Installed Cedega 4.3

2.  Copied the first WoW installation CD to Desktop\cd1

3.  $cedega WoW.exe from within cd1 to start the WoW installer.

4.  Installed WoW just as if in Windows.  *(Swapping CDs worked fine for me)

5.  Downloaded the WoW updates from     [http://www.blizzhackers.com/viewtopic.php?t=261409](http://www.blizzhackers.com/viewtopic.php?t=261409) and manually installed them.

6.  $cedega WoW.exe from within the Wine WoW installation directory.

7.  WoW updated itself to the latest 1.31 build.

From this point, everything has been working great.  I hope this helps some of you.  If you need help, let me know.

---

