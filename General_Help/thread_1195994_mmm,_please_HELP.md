---
title: "mmm, please HELP"
date: 2009-06-24
forum: General Help
---

### Post by xmemox on 2009-06-24
Hi, I have a problem like this [http://img36.imageshack.us/img36/7536/dsc01277y.jpg](http://img36.imageshack.us/img36/7536/dsc01277y.jpg) 
Nothing happened, I done nothing, just sat by computer, watched movies, and shut down pc, next day when i turn on my computer after grub, i have this. So any ideas ? Oh btw, I have ubuntu 9.04.

---

### Post by milton1 on 2009-06-24
Best guess: your hard drive had a stroke. Try booting a live cd and see if you can mount and access your drives.

---

### Post by xmemox on 2009-06-24
I found that people had the same problem, and I tried what they suggested, and they suggested to

> basically for one reason or another, grub can no longer find the OS to boot to.

You need to boot off the live CD and mount the local disk. Then compare the grub menu, fstab, and fdisk -l and we can get an idea of what to do.
and 
> If it is the same problem you need to work a few things out.

Boot from the Live CD.

Run sudo fdisk -l The output will be will be a list of your partitions which you need to identify your root partition (usually this is sda1)

You need to mount that partition to access the files:
sudo mkdir /media/root
sudo mount /dev/sda1 /media/root

Browse to /media/root/boot/grub and look at menu.lst and make sure that references the correct sda# value.
Browse to /media/root/etc/ and look at fstab and see if the values are correct (you can also replace the uuid values with the sda# values in the comments),

If that doesnt work you need to run update-grub from inside your disk so with the drive mounted as above:
sudo chroot /media/root/
sudo update-grub

If you have any problems please head to the IRC support channel or file a question in launchpad.

But I get this 

[http://img146.imageshack.us/img146/6906/screenshotocp.png](http://img146.imageshack.us/img146/6906/screenshotocp.png)




**EDITED**


Some more attempts to do something, but unsuccessfully, here some photos:

[http://img222.imageshack.us/img222/3057/screenshotpht.png](http://img222.imageshack.us/img222/3057/screenshotpht.png)

[http://img222.imageshack.us/img222/8814/screenshot1rav.png](http://img222.imageshack.us/img222/8814/screenshot1rav.png)


It would be really nice to get some help, guys...

---

### Post by keastes on 2009-06-24
> **milton1 said:**
> Best guess: your hard drive had a stroke.

Seconded. 

what file system are you using?

years ago I remember reading about rewriting just the superblocks or the inodes ( I don't remember now was 5-7 years ago) would fix a crash like this, think it was for ext2

---

### Post by xmemox on 2009-06-28
my system is ext3. One more photo after try to mount linux partition:


[http://img31.imageshack.us/img31/5549/asd2y.png](http://img31.imageshack.us/img31/5549/asd2y.png)

---

### Post by xmemox on 2009-07-10
So how I understand no one can tell me what was the problem ? Haven't anybody faced with something like that ?

---

### Post by keastes on 2009-07-11
milton suggested and sounds like its true your hard drive crashed, i'm inclined to agree so to fix it would be to either reinstall and if that doesnt work you will have to replace your hard drive 

i held off on posting to see if any one else had input sorry

---

