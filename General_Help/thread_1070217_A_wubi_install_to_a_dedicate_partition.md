---
title: "A wubi install to a dedicate partition"
date: 2009-02-14
forum: General Help
---

### Post by anbusan on 2009-02-14
hello I'm beginner for Ubuntu user I have question about wubi.

I just installed Ubuntu using wubi last week. I'm using D partition (empty NTFS partition) during the installation, after doing some research for wubi I just read the article how to move A wubi install to a dedicate partition using LVPM so my question is :

1) If I already install my Ubuntu using wubi in D thats mean I already using a dedicate partition?

2) If not how to make my Ubuntu to using dedicated partition (I want to use D)? I mean like I should move my wubi to C and move again to D.

that's all thanks :)

---

### Post by azmo35 on 2009-02-15
Hi,wubi is a kind of virtual so no real partitions but if you wanted make a dedicated partition,burn the iso to cd boot from that and follow the steps and this tresd maybe help you,[http://ubuntuforums.org/showthread.php?t=119892](http://ubuntuforums.org/showthread.php?t=119892)

---

### Post by anbusan on 2009-02-15
> **azmo35 said:**
> Hi,wubi is a kind of virtual so no real partitions but if you wanted make a dedicated partition,burn the iso to cd boot from that and follow the steps and this tresd maybe help you,[http://ubuntuforums.org/showthread.php?t=119892](http://ubuntuforums.org/showthread.php?t=119892)

ok thats mean I should uninstall wubi and then install new one with cd boot? before I install using wubi I try to install Ubuntu with cd boot but I just confuse how to make a dedicate partition for Ubuntu during the installation. Then I try to install from windows xp but I got error that the installation cannot reach the data from CD because the error said my CD-ROM has been using by another application....so that why I'm using wubi.

---

### Post by azmo35 on 2009-02-15
First have you played with live cd?
Live cd is something that you can boot from your cd/dvd drive if this doesn't happen you have to check the bios settings [like this fllopy-cd/dvddrive-hdd....]after successfull boot from live cd you can do a clean install but remenber enything on D drive will go.Our you can keep the D drive for storage and install on C with windows,the live cd will do everything for you.

---

### Post by anbusan on 2009-02-15
I have played with Live CD before, I thought when I move my wubi without doing new installation I'll have a real Ubuntu OS because I just update everything on wubi hehe. So from now I should uninstall the wubi first then go to Live CD then install Ubuntu from there right?

Thanks for your help :D

---

### Post by azmo35 on 2009-02-15
Yes,and no you can use [LVPM]("http://ubuntuforums.org/showthread.php?t=438591")to transfer the wubi to a real partition i did that but on a single HDD, i hope this help.

---

### Post by anbusan on 2009-02-15
yes it helped me a lot, thanks ;)

---

