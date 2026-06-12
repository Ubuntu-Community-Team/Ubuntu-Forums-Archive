---
title: "Parallel Port printer won't print"
date: 2006-07-04
forum: Desktop Environments
---

### Post by pksings on 2006-07-04
New install of 6.06 server...with Xwindows stuff added.

Cannot print to parallel printer. Alps MD-1000 that worked fine under Gentoo and Windows (I formatted and installed Ubuntu).   

Is NOT detected by CUPSYS, "no printers detected". I attempted to configure it via the Gnome GUI tool and localhost:631 after adding to groups shadow and lpadmin per previous posting to no avail.

/dev/lp0 does exist, and is detected during boot. 

The port is set as "bidirectional" using 378. and is the standard printer port built into my tyan motherboard. All cables are tested and securely attached.

I am completely stumped..  Any and all help is greatly appreciated.

PK

Edited;  Solved, the foomatic/md2k driver works just fine.

---

### Post by xoros on 2006-07-04
Go to linuxprinting.org and create your own .ppd file to match your printer.

Then set up with the localhost:631 and the file you just made.

It was the only way I got mine to work.

---

