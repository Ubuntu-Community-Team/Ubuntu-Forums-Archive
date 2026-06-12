---
title: "Delete the Dell partition"
date: 2008-02-04
forum: Dell  Ubuntu Support
---

### Post by TWO on 2008-02-04
I'm going to need to re-partition my drive to make space for a Swap partition but the problem is that I can only do a maximum of 4 partitions, of which one is allocated to the Dell Utility partition.

If I delete the partition, will my Win XP functionality be affected in anyway? 

Many Thanks

TWO

---

### Post by herger on 2008-02-04
Hi.
I had the same problem, but I kept the Dell Utility partition.
I solved doing this:
- get GParted live cd on internet;
- delete the "restore" partition of Windows and shift the c: partition close to that of the boot manager  (depending on the size, it can take a lot).
Now to start windows again You will need the installation CD that Dell has given You, but there is no problem, You won't need to install Windows another time (it has only to "understand" the new partition configuration that is different from when You shutted it down).
- in the new free space You can create a /swap and a / partitions to install You Ubuntu distro (You can't have more than 4).
I did this and I have no problems in the dual booting.
Hope this helps, let me know if there is any problem

Herger

---

### Post by TWO on 2008-02-04
> **herger said:**
> Hi.
I had the same problem, but I kept the Dell Utility partition.
I solved doing this:
- get GParted live cd on internet;
- delete the "restore" partition of Windows and shift the c: partition close to that of the boot manager  (depending on the size, it can take a lot).
Now to start windows again You will need the installation CD that Dell has given You, but there is no problem, You won't need to install Windows another time (it has only to "understand" the new partition configuration that is different from when You shutted it down).
- in the new free space You can create a /swap and a / partitions to install You Ubuntu distro (You can't have more than 4).

Herger

Thanks for your suggestion Herger. I think when I come to this though, it might be a bit trickier in that I have my Ubuntu Partition, a WinXP one and then a shared one in between. 
I made the shared partition because of an incident I had earlier last year before I used Ubuntu where my WinXP decided not to boot and I had the task of trying to salvage what I could of my personal files.

(It was because of that that I switched to Linux! I salvaged most of my files via the Knoppix LiveCD.)

So what I'll need to do -once I back my files up- is to reduce the size of one of the partitions then delete the restore partition and go from there...

---

### Post by herger on 2008-03-25
Hi!
Didi You solve Your partition problems?
Regards

Herger

---

### Post by TWO on 2008-03-25
> **herger said:**
> Hi!
Didi You solve Your partition problems?
Regards

Herger

Hi!

I can't begin to tell you the amount of times I have played with the partition set up since my last post! Long story short, I burned the contents of the Dell Partition onto disc and deleted the partition. Deleting it didn't effect anything at all but I currently only have Kubuntu installed, though I am soon going to set up a Dual Boot with WinXP again because I am missing not being able to play my games properly.

But yes, I think it's safe to say that this issue is resolved!

Thanks for your suggestions though. I'm going to take a look at that GParted CD or use the one that they say comes with the (K)Ubuntu Live CD, and increase the size of my Kubuntu partition then go on to install WinXP. I have read up on how to do this -installing Windows AFTER (K)Ubuntu- so I should be fine now.

Thanks once again

TWO

P.S Oh, I forgot to add that I was able to set up a swap partition in the end.

---

### Post by herger on 2008-03-26
Hi!
Pay attention that if You install Windows AFTER having installed (K)Ubuntu or any other distro, Win will delete Your Grub settings and at the boot up You will see only Windows, without the possibility to choosing any other OS.
So You can do 2 things:
1) reload GRUB from (K)Ubuntu cd if You have installed Win after or
2) install (K)Ubuntu AFTER having installed Windows.

Thanks and regards

Herger

---

### Post by TWO on 2008-03-27
> **herger said:**
> Hi!
Pay attention that if You install Windows AFTER having installed (K)Ubuntu or any other distro, Win will delete Your Grub settings and at the boot up You will see only Windows, without the possibility to choosing any other OS.
So You can do 2 things:
1) reload GRUB from (K)Ubuntu cd if You have installed Win after or
2) install (K)Ubuntu AFTER having installed Windows.

Thanks and regards

Herger

Hello!

Thanks for the heads up. I read about that and downloaded a program called  **UNetbootin Super Grub Disk Loader** which can be run in windows and can restore GRUB.

A recent-ish thread: [http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)

And also an Ubuntu help page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-63b2778ea83a8bd980a515b01f45ca3843f23e3e](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-63b2778ea83a8bd980a515b01f45ca3843f23e3e)

provide the information. 

Thanks once again

TWO

---

