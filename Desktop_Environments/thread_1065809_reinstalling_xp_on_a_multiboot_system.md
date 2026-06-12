---
title: "reinstalling xp on a multiboot system"
date: 2009-02-10
forum: Desktop Environments
---

### Post by aladdin83 on 2009-02-10
Hey All.

**_Problem_**:  Reinstalling xp on a multiboot system completely messes up the MBR leaving no choice but to reinstall all other OS from scratch. 

**_Computer Specs and OS order_**:  
       Core 2 duo      (2.2 ghz)
       4 gb ddr2 ram   (800 bus speed)
       320 gb Hard Drive 

After reading many of the tutorials on how to multiboot I decided on this order.  
(1) Microsoft Xp 32bit,    (2) Microsoft Xp 64bit, 
(3) Microsoft Vista 64bit, (4) Ubuntu Intrepid 64bit

Recently I ran into some free time and decided to reinstall  my windows xp32 bit.  But, after installing windows xp. I realized I couldn't get into vista or xp64 bit (duh, it was inevitable).  I know how to install the grub boot loader so getting back ubuntu was a snap.  *Can someone point me in the right direction for reinstalling windows xp32 OS w/out the hassle of reinstalling ALL the other windows OS.* 

I did try to repair Vista and Xp64 but the repair seemed like it reinstalled the OS. I was hoping it would only fix the Boot loader.  

PS: thanks in advance for replies.

---

### Post by jhayes on 2009-02-10
sounds like u have grub on the mbr right now,
with chainloader in there to load windows. you should be able to have 
1. grub boot it all, with the chain laoder option
2. pointed to a boot.ini file, with multiple lines
3. i dont have one handy, but near the end, with the different numbers, multi disk rdisk etc, those are kinda like /dev/sda1 ... /dev/sdb1 etc. 
with some luck, you can add in the lines neccessary to load the 2nd and 3rd windows.

so load winxp 32b, let it eat the mbr. fix grub. then make sure grub has the chainloader pointing back to winxp. then with the correct lines added into the winxp's boot.ini file it should load xp 64, and vista .

the thing that will get you is i think putting grub back on might mess with ntldr, which will be hard to fix.

ps, this problem ended for me with just ubunto + vmware, no dual boot.
2 physical drives should help also.

---

### Post by boban on 2009-02-10
You may use [Super Grub Disk]("http://www.supergrubdisk.org/") for restoring MBR. It even boots from usb (I used [UNetbootin]("http://lubi.sourceforge.net/unetbootin.html") for this).

---

### Post by bregale on 2009-02-10
sounds like you want quite a few os on your system, the way i think you should approach this is to partion your drive into 4 or have a two hard drives partioned,
   then install xp first then install vista ,after that you  can install ubuntu through windows, 
       good luck

---

### Post by aladdin83 on 2009-02-11
Thank you All for the replies.

I guess the best solution for me to is use a 3rd party boot loader.  I'm thinking Super Grub might do the trick.

---

### Post by boban on 2009-02-11
> **aladdin83 said:**
> Thank you All for the replies.

I guess the best solution for me to is use a 3rd party boot loader.  I'm thinking Super Grub might do the trick.

Hmm... I do not think that this way you'll be using "3rd party boot loader". I suggested to use grub as a main bootloader :), but in case windows (or other OS) overwrites your MBR you can repair/reinstall grub using Super Grub Disk. Customising grub is not that hard - at least with combination of windows + linux. It comes to editing file /boot/grub/menu.lst (it may depend on distribution, but this is the place where Ubuntu keeps menu.lst).

---

