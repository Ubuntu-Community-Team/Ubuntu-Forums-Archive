---
title: "Debian 7.4.0 onto HW raid 5"
date: 2015-02-09
forum: Debian
---

### Post by Drenriza on 2015-02-09
I have bought a rocketraid 2710 HW raid controller and converted four 2TB drives to a single raid 5.

In BIOS the raid controller is seen as 1 physical disk, but when i go through installing Debian it sees it as four individual 2 TB disks.

Im not really sure what i'am missing, do you need to do something extra to install a Debian system through a raid controller?
If you have any good material / guides / other on installing Debian onto a raid system please share with me.

Thanks on advance.
Kind regards.

---

### Post by Drenriza on 2015-02-09
I read this article
[https://www.debian-administration.org/article/512/Software_RAID5_and_LVM_with_the_Etch_Installer](https://www.debian-administration.org/article/512/Software_RAID5_and_LVM_with_the_Etch_Installer)

but havent got much wiser if this creates a raid 5 system

---

### Post by Pumm4 on 2015-02-09
Hi Drenriza,

This might shine some light on your situation:

[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)
[http://serverfault.com/questions/397646/raid-5-with-4-disks-on-debian-automatically-creates-a-spare-drive](http://serverfault.com/questions/397646/raid-5-with-4-disks-on-debian-automatically-creates-a-spare-drive)


Good luck!

---

### Post by Drenriza on 2015-02-09
Thanks for the links Pumm4

Did they install Debian on one disk and than create the array afterwards?

---

### Post by Pumm4 on 2015-02-09
Good question, by default since you have a hardware RAID it should be easier installing any *NIX system in one go.

Give it a try.
[SIZE=2][I]

[SIZE=2][COLOR=#a52a2a]Edit1[/COLOR]: Links we both found were configuration guides for Software RAID[/SIZE][/I][/SIZE].

---

