---
title: "[SOLVED] Dell Inspiron 1525n wireless nightmare 3945ABG"
date: 2008-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by danbob on 2008-11-15
I'm relieved this is finally solved. I've been pulling out my hair for 2 weeks. A short rant first...

Dell gave both themselves and Ubuntu a bad name by shipping laptops pre-installed with Ubuntu 8.04.1 Hardy, guaranteed to work out of the box (!), with faulty built-in wireless drivers. Very difficult to get any kind of Ubuntu support from Dell at all, and such that I did get (update the BIOS, for one) did nothing to solve the problem.

Step by step to fix this for the beginner:
1) Go into the BIOS at bootup (f2 key), find the 'wireless switch' information. Disable the wireless switch completely for all functions.
2) While you are in there, set the boot order to CD/DVD first, so you can re-install the OS.
3) Get the latest Ubuntu CD (8.10) or download it using your wired connection and burn an ISO image CD.
4) Boot and install 8.10 off the CD.
5) Solved!

The thing that triggered this whole nightmare was simply booting up the machine, running 8.04.1, out of the box with the wireless switch OFF. That disables the wireless card completely until you re-install the OS. However, even re-installing 8.04.1 didn't help--it could find the wireless card, but signal strength was always zero on every network. I tried ndiswrapper and the correct driver for the 3945ABG right from Intellinux, and once again the wireless card was completely disabled. Arrgh!

Fortunately, 8.10 solves the problem. 


NOTE: The wireless card switch is still an issue in 8.10 with the 3945ABG card, according to the release notes! Hence my instructions above to completely disable the switch. It's way too easy to accidentally trip it while putting the laptop into or out of its case. I'm sure this will get fixed in later releases of Ubuntu.

#-o
DAN

---

