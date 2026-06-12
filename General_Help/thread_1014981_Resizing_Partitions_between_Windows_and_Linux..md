---
title: "Resizing Partitions between Windows and Linux."
date: 2008-12-18
forum: General Help
---

### Post by jfl on 2008-12-18
Hi,

I have a recent IBM laptop on which I installed Ubuntu 8.04 dual booting with windoze XP.
Now I am using Linux 90% of the time; I still have to use XP for flight planning software (I am a corporate pilot).

Question:  What is the best way of resizing the partitions ?
I have 3 NTFS partitions C: Sysytem   D: Apps  E: Data
and 3 Linux:  / , /home,  and swap

I need to make my /home bigger by taking a few Gb from NTFS E:

Should I use Partition Magic v8.0 under XP or gparted under Ubuntu, or something else I don't know about ?

Thanks !

---

### Post by taurus on 2008-12-18
You need to use gparted from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Don't forget to backup your files first.

---

### Post by sPiN1 on 2008-12-18
I would suggest booting up to an ubuntu live disc and going into sudo gparted and doing it from there, change the sizes, hit apply and restart. I wouldn't suggest blindly doing it though I would read up on resizing partitions first so you don't break something.

---

### Post by jfl on 2008-12-18
Is it safe to modify NTFS partitions with "gparted" ?
I thought I remembered a thread from last year about messing up the windows partition table.

Maybe I should shrink my NTFS partition from windows (partition magic) and then use gparted to grow the /home partition.
Right now I don't have the time to have to tinker after I did something wrong ;-)

---

### Post by vanadium on 2008-12-18
It depends on your current partitioning what you can do and what not. You might want to post the output of the command "sudo fdisk -l".

---

### Post by PocketDog on 2008-12-18
I'd definitely use a Windows partitioner for this. As good as Gparted is (very), NTFS can easily be corrupted using it unless it's very, very tidy via defragging.

---

### Post by binbash on 2008-12-18
for windows partition resizing, use a windows based softwares like paragon partition manager, for other stuff use gparted live cd

---

### Post by vanadium on 2008-12-19
Use gparted only for partitioning. If you mix partioning programs, you might need to repartition the whole drive at one time.

---

