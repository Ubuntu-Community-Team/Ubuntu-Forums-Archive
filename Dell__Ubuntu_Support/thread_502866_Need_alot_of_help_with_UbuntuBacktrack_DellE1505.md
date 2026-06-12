---
title: "Need alot of help with Ubuntu/Backtrack DellE1505"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by jmiller0526 on 2007-07-17
Ok let me start by telling you (probably obviously by the fact i am posting here) that today is my first day using anything LInux based

also i know this has alot more to do with Back track than it does with Ubuntu, but it seems to be aleast a good starting point, you people seem to be pretty damn good at this stuff...



Ill start from the beggining....

I have a Dell E1505 with the ATI card (1400 im pretty sure)
I had it set up to dual boot XP and Vista

I decided i wanted to run sum linux and had herd alot about Ubuntu
I had a lot of trouble with this whole Xserver issue, but got it to work using some scripts from mylittleubuntu.com  everything went fine from there, i could succsesfully boot into either xp/vista/or ubuntu....

i started poking around at alot of stuff and found the Back Track 2.0 on the internet, i ran the live CD and it worked great so i went back and made another partition for it

I installed it fine, reboot the system and then things got REALLy ugly

first off, i must be missing something but i can seem to find ANY way to boot into anything else but BT unless im using a CD (im currently using the Ubuntu live cd)

now if that wasnt bad enough Back track (the only thing i can boot into) doesnt like to play nice with the Dell Either giving me the same BS about this dang xserver
i have tried numerous things that most likely didnt help at all but is really the only things i new how to do just because i had to deal with this Xserver with ubuntu (remember im NOT a linux guy)

I logged into BT and first tried to use the "ati" command (worked fine when booting off the bd)- it gave me a fatal error 10
then i tried to use the generic versa driver by using the "startx" command - same error as before

i tried the xconfig which bt didnt recognise and had me use "xsetupconfig" which seemed promising but also didnt work

then as a last ditch effort i tried the same scripts i used to get Ubuntu to work again to no avail....

i have no idea what im doing or really what you guys need to help me if i can be saved at all


so im stuck no using the Live ubuntu cd untill some guru can come in and put me in school.....

its 2:30 am here, ive been working on this for hours, and of course didnt write anything down so its all of memory so please forgive me if you guys need more details or something i said just isnt right....

PLEase guys you gotta help me:confused:

then i tried to use the

---

### Post by constrictor on 2007-07-17
I am not sure if this will help but if you're having trouble with your xserver not being able start up even with the liveCD then there is a little howto [http://www.mylittleubuntuguide.com/](http://www.mylittleubuntuguide.com/) and a few scripts that automatically set up your graphics card to work with Ubuntu.

Hope this helps

---

### Post by jmiller0526 on 2007-07-17
Yeh, thats how i initially got Ubuntu to work, but now that i isntalled backtrack i cant get it nething to work because i can only boot to backtrack....and it doesnt work with the guide

---

### Post by digitalbenji on 2007-07-17
I recommend using Ubuntu as your primary OS for a little while before you start worrying about backtrack.  Just install Ubuntu off the livecd, or, off the alternate install cd.  Backtrack is a dangerous tool, and I get the impression that most people simply want to use it to do nefarious things.

---

### Post by Ethernull on 2007-07-18
I am running a tripple boot of XP, UbuntuStudio and Back|Track 2 on a laptop with an ATI card.

Here is the process:

Install XP
Install Ubuntu, set the bootloader to the MBR (so that Grub boots and gives a choice of XP or Ubuntu)

Install Backtrack, but set the bootloader to the partition that backtrack is in.

Boot into Ubuntu

Edit your /boot/grub/menu.lst to add a line for chainloading backtrack.

Ubuntu likes grub, backtrack likes lilo for booting.

In the menu.lst, at the bottom, you need to make an entry for Backtrack that looks like the entry for XP, but the partition needs to point to the BT one.

If you can only get into Backtrack, I would just reinstall as above. Its really a pain to get a backtrack created lilo.cong to boot ubuntu correctly. Otherwise, there were some posts on the BT forums, but they didnt work for me.


Your startx problems have to do with the ATI FireGL drivers.
For Backtrack, go to the backtrack wiki, in the how to section and find the entry regarding ati.lzm

The ati.lzm file can be downloaded from the backtrack site under the link "modules"

You need to download that into your root directory in BT, untar it by following the instructions on the how to page, then run the script that it makes. WHen that is done you need to run aticonfig from the console.

Look at the output of aticonfig and it will tell you the command to use to get it set up the first time. I dont recall it exactly, but it will print on the screen. 

Then you can startx in Backtrack and have a resolution of 1440x900 with 3d acceleration :)

Good Luck

---

### Post by Posterus on 2007-11-27
Ethernull,
     First off good job on the clear instructions, some threads are less understandable.

(sorry if this is stealing the thread but...)I first had Ubuntu as the only OS on my Alienware area 51 -5500 laptop and then i installed XP as a dual boot and it went fine.  Then i installed Back Track 2, after that i rebuilt grub so now i can get into either XP or Ubuntu but for some reason i cant get into back track.  I think it has something to do with my menu.lst file.  When i try to boot into back track it gives me an Error 13.

here's the bottom part of my menu.lst
> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ddf52bb-b051-4381-9363-9302e88c49b1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ddf52bb-b051-4381-9363-9302e88c49b1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7ddf52bb-b051-4381-9363-9302e88c49b1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7ddf52bb-b051-4381-9363-9302e88c49b1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
	Other Operating Systems----------- 

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

#
#
#

title		Back|Track 2
root		(hd0,3)
makeactive
chainloader	+1

---

