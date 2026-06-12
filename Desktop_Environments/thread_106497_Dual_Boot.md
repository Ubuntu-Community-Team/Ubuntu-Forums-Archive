---
title: "Dual Boot"
date: 2005-12-20
forum: Desktop Environments
---

### Post by oLeWuLF on 2005-12-20
I am running Windows XP on a 40 Gig NFTS formatted HD and want to make the  leap to Ubuntu. My problem is I only have 8 gig left and I really want to keep XP and linux separate.

I have a fresh 40 GIg drive just waiting to be used and would like to load Ubuntu on that and dual boot from two hard drives.

Here's my plan:

disconnect the current drive
install new drive and set up Ubuntu
Reinstal new drive and.......................

that long pause is what now..my bios wont let me select the a boot option every time i start up. I don't want to change the bios settings every time i want to use linux..

There must be a boot software which allows me to select which drive but i'm not sure which one to use. 

I really want to keep these os seperate..i have no need to share files or any settings between the two drives..it should act liek two totally seperate systems when done.

Any suggestions..

Chris

---

### Post by johnfs on 2005-12-20
a dual boot system are on  the same drive.split the drive you have xp on c and ubuntu on f.

---

### Post by oLeWuLF on 2005-12-20
I know i can split the original drive..I am trying to avoid that with only 8 gig left on my original drive and i really don't want to confuse my wife ("uhhh how do i save this document") with adding more storage on another drive. I just want the option to point to the second drive on startup and use it independantly. Maybe it's stupid and not possible.

Ole

---

### Post by nickj6282 on 2005-12-20
I can't say for 100% sure as far as Ubuntu goes, but other Linux distros will set up dual boot automatically. Here's what you should do:

1. Install the second HDD into your PC.
2. Put the Ubuntu disc into the drive and start the installation.
3. Format the second hard drive and install Ubuntu for it, make sure you tell it to leave the first hard drive alone.
4. Ubuntu, if it's anything like other Linux distros, will install a bootloader (probably Grub, possibly Lilo, doesn't matter really) which will let you choose to start Windows or Ubuntu at boot time.

I'm sure someone else can verify whether or not Ubuntu will install a boot loader set up to boot Windows and Ubuntu on the same PC.

-Nick

---

### Post by oLeWuLF on 2005-12-20
Ok...yeah, that should work...I must be making this too complicated..Thanks for the info.

Ole

---

### Post by rudeboyskunk on 2005-12-20
or you could just do like me, who gets frustrated every time i try to do dual boot with any linux and my other hard drive (windows 98 -- i only  have it on there so i can play world of warcraft and am too lazy to do the whole cedega thing), and just access BIOS every time i need to get to windows98.  seriously, it doesn't matter what linux distro, dual boot never works (though it did work the very first time i ever used linux, which was debian and windows xp dual boot).

that's my rant.

---

