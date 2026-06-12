---
title: "I need something like Partition magic for Linux"
date: 2008-12-31
forum: General Help
---

### Post by Johnny-Cache on 2008-12-31
I need to be able to move around my partition sizes without deleting my data.  Suggestions?

---

### Post by sovietdoughnut on 2008-12-31
get gparted from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

you can burn a live disk to boot from a cd and it will allow you to resize your partitions. it's free and open source =)

---

### Post by ajcham on 2008-12-31
Most Linux live discs have a partition editor readily available - if you are using ubuntu, and still have the disc, just boot into the live environment and go to **System » Administration » Partition Editor** to start gparted.

---

### Post by 2hot6ft2 on 2008-12-31
> **Johnny-Cache said:**
> I need to be able to move around my partition sizes without deleting my data.  Suggestions?
First it's already installed so there's no reason to download it.

Second It's already on the livecd you used to install ubuntu.

Third You're going to have problems trying to resize partitions you have mounted by running it from your install and since you can't unmount the drive your working in there's 4th.

Fourth Boot from the livecd and once at the desktop go to System>Administration>Partition Editor and do your resizing. When finished close the Editor and reboot removing the disc when it tells you to.

Fifth boot up normally and it's all done.

6th there isn't a 6th

---

### Post by dcstar on 2008-12-31
> **2hot6ft2 said:**
> 
........
6th there isn't a 6th

6th is look in the forums because the question has been asked - and answered - about 1,000 times previously.

---

### Post by wolfen69 on 2008-12-31
> **2hot6ft2 said:**
> First it's already installed so there's no reason to download it.



gparted is not included on the intrepid cd. i know, i just tried.

---

### Post by ajcham on 2008-12-31
> **wolfen69 said:**
> gparted is not included on the intrepid cd. i know, i just tried.

Which CD are you using? It's definitely on my disc [SIZE="1"](ubuntu-8.10-desktop-i386)[/SIZE] — I double checked yesterday evening when another user stated he couldn't find gparted on his live disc.

---

### Post by Johnny-Cache on 2009-01-02
7th - thanks for the help

---

