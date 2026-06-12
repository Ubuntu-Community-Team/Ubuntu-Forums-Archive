---
title: "Dual boot Windows 7 after Ubuntu 11.04"
date: 2011-05-30
forum: Desktop Environments
---

### Post by rigel4 on 2011-05-30
Sorry if this has been asked before , but i have searched and can't find what i need.
I have Ubuntu 11.04 on my computer and very happy with it.
I would like to play a few games as well, to be honest i only play one,
UT2004, I tried it on virtual machine , however the results were disappointing.

I would like to know how to dual boot windows 7 with Ubuntu 11.04 after Ubuntu has been Installed.
I don't want to start again if possible.

Thank you

---

### Post by 3Miro on 2011-05-30
Windows 7 requires two partitions, one primary and one primary or logical. It may be tricky to tell the windows installer which partitions to use, I am not sure.

Once you install Windows, it will destroy the Linux boot loader and you will have to reinstall it:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
(look for reinstalling Grub 2)

IMO the best way to dual-boot windows and Linux is to have two separate HDD, it is a little bit easier then, but not everyone has that option.

---

### Post by rigel4 on 2011-05-30
> **3Miro said:**
> Windows 7 requires two partitions, one primary and one primary or logical. It may be tricky to tell the windows installer which partitions to use, I am not sure.

Once you install Windows, it will destroy the Linux boot loader and you will have to reinstall it:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
(look for reinstalling Grub 2)

IMO the best way to dual-boot windows and Linux is to have two separate HDD, it is a little bit easier then, but not everyone has that option.

Thanks for your reply, I might have a second disk around not sure.
If i do could you advise me on best practice.

I have Ubuntu on a root/home partition, which more than likely makes the procedure a bit more complicated.

EDIT:On second thoughts I have an xp disk would that make things any easier

---

### Post by 3Miro on 2011-05-30
I can tell you how to do two HDD, it is not very hard at all. Then you can do Windows 7 and Ubuntu.

XP would be easier. All you need to do is point XP to the partition where you want to put it. XP uses only one primary partition. You can use a Ubuntu liveCD to shrink an existing partition and/or make a new one (use System -> Admin -> Gparted).

Windows 7 should be doable as well, it is just that 7 does something weird with one of its partitions and it may or may not cause trouble. I don't know enough about 7 to help.

At any rate, you should backup important data from your HDD first. When you mess with partitions, it can always potentially end up in a disaster.

---

### Post by rigel4 on 2011-05-30
> **3Miro said:**
> I can tell you how to do two HDD, it is not very hard at all. Then you can do Windows 7 and Ubuntu.

XP would be easier. All you need to do is point XP to the partition where you want to put it. XP uses only one primary partition. You can use a Ubuntu liveCD to shrink an existing partition and/or make a new one (use System -> Admin -> Gparted).

Windows 7 should be doable as well, it is just that 7 does something weird with one of its partitions and it may or may not cause trouble. I don't know enough about 7 to help.

At any rate, you should backup important data from your HDD first. When you mess with partitions, it can always potentially end up in a disaster.


Thanks.
I'll get back to you later, need to go shopping right now.
I think i hunt around and find a extra disk before i proceed .

---

### Post by 3Miro on 2011-05-30
> **rigel4 said:**
> Thanks.
I'll get back to you later, need to go shopping right now.
I think i hunt around and find a extra disk before i proceed .

Let me know if the second HDD is SATA or IDE.

---

### Post by darkomano on 2011-05-30
If you install Windows 7 to a disk where partitions already present 
a) Windows 7 installs itself to the partition chosen by the user.
b) but puts the Windows 7 boot environment always on the active partition.
If the chosen partion is also the active partition then Windows 7 install puts everything on this partition only.
 
By default every Windows version (XP, Vista, 7) installs its boot environment to the active partition as Windows boot sequence is always: 
MBR -> active PBR(partition boot rec) -> boot manager(or nt loader) -> next stage of OS chosen (when dual-boot).
 
Grub (legacy and 2) does not care about "active" partitions.:)

---

### Post by 3Miro on 2011-05-30
> **darkomano said:**
> If you install Windows 7 to a disk where partitions already present 
a) Windows 7 installs itself to the partition chosen by the user.
b) but puts the Windows 7 boot environment always on the active partition.
If the chosen partion is also the active partition then Windows 7 install puts everything on this partition only.
 
By default every Windows version (XP, Vista, 7) installs its boot environment to the active partition as Windows boot sequence is always: 
MBR -> active PBR(partition boot rec) -> boot manager(or nt loader) -> next stage of OS chosen (when dual-boot).
 
Grub (legacy and 2) does not care about "active" partitions.:)

Are you sure you can have Windows 7 on only one partition?

I have never seen Windows 7 installed on only one partition. I thought it always uses at least two. It even did that when I selected the option to just use the entire disk.

(Grub sets its own active partition, yet it doesn't care about the dos boot flag)

---

### Post by wildmanne39 on 2011-05-30
> **rigel4 said:**
> Sorry if this has been asked before , but i have searched and can't find what i need.
I have Ubuntu 11.04 on my computer and very happy with it.
I would like to play a few games as well, to be honest i only play one,
UT2004, I tried it on virtual machine , however the results were disappointing.

I would like to know how to dual boot windows 7 with Ubuntu 11.04 after Ubuntu has been Installed.
I don't want to start again if possible.

Thank you
Hi, here is a guide to dual boot windows when ubuntu is installed first.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1) This one is incase you decide to put windows on a second drive.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by tungharley_t3 on 2011-08-13
hey guy from vietnam.

i have a problem.

i do install wubi ubun 11.04 in win 7.

boot time n choose make me annoy, so i change option in win 7 : boot time = 0 ; default OS : ubun .

now i cannt boot 2 win 7 , grib selection " win 7 loader spa2 " doesnt work .

i have try start-up manag, update grib 2, etc, but it doesnt work .

any help , thanks . 

have a 9 day !

---

### Post by WiCkD1 on 2011-08-13
I've never had luck installing windows as a dualboot AFTER having a linux distro install, but I must say, my Windows 7 desktop, installing dualboot ubuntu was easier than putting butter on a toasted slice of bread! :-)

---

