---
title: "Herd3 on Intel S3000AH board"
date: 2007-02-12
forum: Development CD/DVD Image Testing
---

### Post by Patje on 2007-02-12
Hi all,

Ubuntu 7.04 Herd3 does not work on this board. After starting X you hold a nice black screen. The system is not frozen, just a black screen. Debian Etch beta works fine if you downgrade the standard 24bit resolution to 16bit.

The onboard chipset on this board is the ATI Technologies INC ES1000.

---

### Post by Henrik on 2007-02-13
Hi Patje,

Please file a bug on X here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bugs](https://bugs.launchpad.net/ubuntu/+source/xorg/+bugs) and attach /var/log/Xorg.0.log (ideally do some searching first to see if it has already been reported)


Is this a regression? Has it worked on previous versions of Ubuntu?

---

