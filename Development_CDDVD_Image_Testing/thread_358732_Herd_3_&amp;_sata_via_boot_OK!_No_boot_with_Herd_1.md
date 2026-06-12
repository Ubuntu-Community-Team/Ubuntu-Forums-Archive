---
title: "Herd 3 &amp; sata_via boot OK! No boot with Herd 1-2"
date: 2007-02-11
forum: Development CD/DVD Image Testing
---

### Post by luca.mg on 2007-02-11
Sorry for the thread's title in broken english, but that's it: it used to be impossible to boot a system with a PCI Via VT6420 sata controller with the Herd 1 and 2 test disks, same problem with any distro I came across  sporting kernel 2.6.18 and 2.6.19: Fedora, Suse, many Debian based live CDs. Everithing seems to be back to normal with Herd 3, and I'm glad to carry good news instead of a rant. This is the output of uname -rm: 2.6.20-6-generic i686. Another previously unbootable system with an embedded Via VT8237 sata controller boots fine too. As a long time gnu/linux user it's the first time I can see a broken module surviving 2 major kernel revisions and I hope that the next Ubuntu release will keep a working kernel. 

TYFYA 

luca

---

### Post by cstrippie on 2007-02-11
Must be directly related to your controller: my laptop uses SATA and has had no boot problems under edgy or feisty.

---

### Post by luca.mg on 2007-02-12
"Must be directly related to your controller" 
of course it is, there's plenty of postings in several linux forums across the net, this is only to say that the problem is gone! 

peace luca

---

