---
title: "Windows XP not starting anymore after installing ubuntu. Please help!"
date: 2009-03-22
forum: General Help
---

### Post by BramWillemsen on 2009-03-22
Hello everyone,

I decided to put ubuntu on my desktop today, but i want to keep windows for playing some games that are not natively supported by linux. Like some other people, the install cd gave some I/O errors (maybe i burned at a speed too high) so i decided to unpack the contents of the .iso file on a 9 gig partition of mine. I double clicked on the setup program inside windows. Since i could not boot from this 9 gig drive normally, I clicked on the "help booting from cd and then restart windows" option. When i restarted my computer it started ubuntu from a live CD it said. There was no cd in my drive so i assume it just started from the small 9 gig partition. When this test ubuntu booted it initiated the real install process. 

During this process my main partition (500 gig) was split into two parts. One of 300 gig for windows and a 200 one for ubuntu. The install went very smooth. When the computer restarted the boot load showed up as expected (this is grub right?). Ubuntu boots with no problem, but ** windows does not start anymore! it only says "starting up ..." **. I don't have much ubuntu experience yet, but after browsing around I saw that other people had similar problems too. They suggested changing something in /boot/grub/menu.lst . The bottom part of the file is like this

-------------------------------------------

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f4b1994c-75d7-405e-b582-7d2cefe921f3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f4b1994c-75d7-405e-b582-7d2cefe921f3 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f4b1994c-75d7-405e-b582-7d2cefe921f3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f4b1994c-75d7-405e-b582-7d2cefe921f3 ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f4b1994c-75d7-405e-b582-7d2cefe921f3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

-----------------------------------------------------------------

When i'm in linux and looking at the 300 gig partition containing windows XP, there seems to be nothing wrong. All the files are still there. ** somehow grub doesn't connect with windows, the files are still intact on this new partition that was created during the installation of ubuntu ** Can anyone please help me out ? I don't really know much about grub and if i'm going to experiment things might really break. 

Thanks for all the suggestions ! Bram

---

### Post by sdowney717 on 2009-03-22
do you have a windows xp setup cdrom disc?
if so, then you can boot it and run "fixmbr"
search for the command on google.
If this restores windows xp boot, then you will need to restore the 
grub boot loader to get the boot menu back to be able 
to select between XP and ubuntu.
which is another set of commands.
but see if you can restore xp boot first before worrying about grub

HOPEFULLY, you did a defrag on windows before splitting the partitions.
It is possible you overwrote something windows needed to boot up.
In which case, you will have to reinstall XP.

---

### Post by meierfra. on 2009-03-22
the Starting Up error often means that you have to fix the Windows boot sector:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

---

### Post by meierfra. on 2009-03-22
I have never seen a "starting up" error being fixed by ""fixmbr" and "fixboot". 
After fixmbr  you probably still won't be able to boot into XP. So I recommend to try "testdisk" first.

---

### Post by BramWillemsen on 2009-03-22
> **sdowney717 said:**
> do you have a windows xp setup cdrom disc?
if so, then you can boot it and run "fixmbr"
search for the command on google.
If this restores windows xp boot, then you will need to restore the 
grub boot loader to get the boot menu back to be able 
to select between XP and ubuntu.
which is another set of commands.
but see if you can restore xp boot first before worrying about grub

HOPEFULLY, you did a defrag on windows before splitting the partitions.
It is possible you overwrote something windows needed to boot up.
In which case, you will have to reinstall XP.

yes i did defragment before i partitioned :) I'll try the testdisk option suggested by meierfra. Thanks for the quick replies guys! I will keep you posted of the results

---

### Post by sdowney717 on 2009-03-22
if you have any data you want to keep, you should perhaps move it into the ubuntu partition. XP puts your user data in documents and settings user folder which will get wiped out if you reinstall xp.
I always thought that was dumb.
Good luck, try all the options before giving up.

---

### Post by BramWillemsen on 2009-03-22
> **meierfra. said:**
> the Starting Up error often means that you have to fix the Windows boot sector:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

It worked!!! i'm posting this message inside windows XP :) The boot sector was damaged but windows runs fine again now thanks to your suggestion. you deserve a medal ;)

---

### Post by meierfra. on 2009-03-22
> It worked!!! i'm posting this message inside windows XP

Good news.  Have fun with Ubuntu and XP.

---

### Post by Luca_turicci on 2009-05-16
> **meierfra. said:**
> the Starting Up error often means that you have to fix the Windows boot sector:

Download the [testdisk-6.10.linux26.tar.bz2 package]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") to your Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

HI, It doesn't give me the option to Write, what should i do?
Is not like i need windows, but my friends are annoying me with "Wtf is that? where's the "Start" button?" thing...

---

### Post by swmail on 2009-12-10
> **meierfra. said:**
> 
Thank you very much! It's really works! Great!

---

### Post by Digidon on 2011-01-19
Hi
Just had same problem, downloaded Testdisk and went though as you said 
now up and running
Thanks

Don

---

