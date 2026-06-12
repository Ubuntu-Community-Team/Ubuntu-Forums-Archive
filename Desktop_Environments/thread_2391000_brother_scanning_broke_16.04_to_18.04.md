---
title: "brother scanning broke 16.04 to 18.04"
date: 2018-05-04
forum: Desktop Environments
---

### Post by derekcentrico on 2018-05-04
Okay, so I followed all I could online.  I installed the same DEB files and what not as originally available for my MCF-J925DW which worked on 16.04.

The scanner app will start scanning via the machine with the documents feeding, it always crashes, and the documents feed rapidly through the printer to no success.

 brscan-skey -l MyScanner         : brother4:net1;dev0  : 192.168.1.200        Not responded


Installed aside from APT sane packages are:
brscan-skey-0.2.4-1.amd64.deb
brother-udev-rule-type1-1.0.2-0.all.deb
mfcj985dwcupswrapper-1.0.0-0.i386.deb
mfcj985dwlpr-1.0.0-0.i386.deb
brscan4-0.4.4-4.amd64.deb

The "installer" script will not run because the MCF model is not acceptable to it.  "linux-brprinter-installer-2.1.1-1"

Any thoughts out there on how to resolve?

---

### Post by him610 on 2018-05-06
derekcentrico,

> MCF model is not acceptable
It probably should be ***MFC***

Checked the Brother website, nearest models to yours is either of these two...
MFC-J825DW or MFC-J985DW(XL)

---

### Post by derekcentrico on 2018-05-07
LOL.  Good catch...and what a whirlwind that day was.  Had to tweak some stuff that was lost in the upgrade such as somehow my PGL configuration which had 192.168.1.0/24 whitelisted.  After running the script and fixing my iptables we have printing and scanning again.  Thanks for the good eye on my typo.

---

