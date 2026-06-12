---
title: "Hard drive Imaging?"
date: 2008-12-11
forum: General Help
---

### Post by evilbuntu on 2008-12-11
I have 8.04 server running on a hard drive set up with an xp pro dual boot. 

**I wish to image the entire drive with both partitions and everything (there are actually 3 partitions because i have VMWare running another xp pro inside ubuntu).**

Is there something i can use to do this and how would it be used. someone gave me a copy of acronis for windows to try that supposedly had a linux client in it but i could not get the stupid thing to work right. i would almost rather have something i could run stand alone inside of ubuntu, copy the whole hard disk and have a recovery cd incase my server ever crashed out on me.

thanks

i use ghost 14 on my windows machines stand alone each with their own liscence. i could never get them to talk to each other over my network. they see each other fine but wont communicate, i get the stupid windows rcp error and have tried everything to rectify that but its no big deal for me.

---

### Post by jerome1232 on 2008-12-11
Well there's quite a few programs that can do this for you.

dd - a commandline utility that copies bits, will require that you read up on how to use it type 'man dd' to pull up it's man page, an example if you wanted to image hard disk sda to a file would be similar to the code below. If you wanted to  compress the image files or send them over the network you need seperate utilites like netcat and bzip ```
sudo dd if=sda of=hardiskimage.img bs=10M conv=notrunc
``` 

PING (Partimage is not ghost) - This is some imaging software that can do the job faster than dd, it doesn't read the blank space and can compress the resulting image file. Also has built in support for sending the images  across a network.

---

### Post by howefield on 2008-12-11
> **evilbuntu said:**
> .... someone gave me a copy of acronis for windows to try that supposedly had a linux client in it but i could not get the stupid thing to work right.

I use Acronis True Image and it works a treat, from the windows install, I created a bootable cd and only ever use that. It's fast, accurate and easy.

There is one caveat, in that acronis will only copy 8.10 installs bit by bit (leading to huge backup files) since Ubuntu changed the inode size. As a workaround I use an 8.04 cd to partition the drive, then install 8.10, this seems to keep everything sweet with True Image.

---

### Post by evilbuntu on 2008-12-11
are you using acronis for windows or ubuntu?

i am not really worried about send the image over the network, i have SAMBA set up and can do that myself after wards from the mapped drives.

thanks for the replies so far. also if from windows are you running a dual boot and the acronis from the windows partition, if you are; when you have to restore it will it keep the GRUB boot order i have as Ubuntu as the primary.

thanks again :) this forum is always a huge help

---

### Post by Dusenberg on 2008-12-11
> **evilbuntu said:**
> I have 8.04 server running on a hard drive set up with an xp pro dual boot. 

**I wish to image the entire drive with both partitions and everything (there are actually 3 partitions because i have VMWare running another xp pro inside ubuntu).**

Is there something i can use to do this and how would it be used. someone gave me a copy of acronis for windows to try that supposedly had a linux client in it but i could not get the stupid thing to work right. i would almost rather have something i could run stand alone inside of ubuntu, copy the whole hard disk and have a recovery cd incase my server ever crashed out on me.

thanks

i use ghost 14 on my windows machines stand  alone each with their own liscence. i could never get them to talk to each other over my network. they see each other fine but wont communicate, i get the stupid windows rcp error and have tried everything to rectify that but its no big deal for me.

I  use acronis true image and have recovered a dual-boot laptop and dual-boot pc. I only image whole partitions onto external hard drive so don't care about os specifics, and do it from 'live' acronis cd so everything is quiet. Easy to use and works. :p

---

### Post by evilbuntu on 2008-12-11
> **Dusenberg said:**
> I  use acronis true image and have recovered a dual-boot laptop and dual-boot pc. I only image whole partitions onto external hard drive so don't care about os specifics, and do it from 'live' acronis cd so everything is quiet. Easy to use and works. :p

do you have a specific version of acronis that works well for you?

---

### Post by howefield on 2008-12-11
> **evilbuntu said:**
> are you using acronis for windows or ubuntu?

i am not really worried about send the image over the network, i have SAMBA set up and can do that myself after wards from the mapped drives.

thanks for the replies so far. also if from windows are you running a dual boot and the acronis from the windows partition, if you are; when you have to restore it will it keep the GRUB boot order i have as Ubuntu as the primary.

thanks again :) this forum is always a huge help
It is the Acronis for windows I use, or more specifically a bootable cd created from an Acronis windows install, the cd supports all sorts of file systems and backup locations.

I no longer have windows on my machine other than a vm, but the bootable cd takes care of imaging just fine whether it is linux or windows or both
on the hard disk.

---

### Post by adamyoungnc on 2009-01-04
Hi - 

I am having a lot of trouble with cloning my dual boot disk (XP and Kubuntu 8.10).  I have spent hours trying to figure this out, but no luck...

I attempted to clone the full disk with Acronis True Image Home 2009.  When the clone completed, kubuntu worked (I could boot kubuntu from grub), but xp hangs up at the "Starting Up..." black screen.  There are a ton of forums on this, and I have spent hours with Acronis in online chat, but nothing is working.  

I believe the problem has to do with the boot order changing (maybe something with fstab or menu.lst?)

Any help would be appreciated. (I will output my menu.lst upon request, but didnt want to make this first post too long)

---

### Post by redroad55 on 2009-01-12
A couple of questions..Did you set up acronis secure zone prior to clone attempt (giving you f11 at boot)?..Also recently I discovered that in Xp pro sp3 when I attempt to clone the hard drive it forces me to reactivate windows , where in sp2 that requirement was not there .. Did you install xp 1st and then your ubuntu .. I have successfully cloned this way with acronis 11 .. please keep this thread going so we can learn with you .. thanks

---

### Post by hangfire on 2009-01-12
> **evilbuntu said:**
> **I wish to image the entire drive with both partitions and everything (there are actually 3 partitions because i have VMWare running another xp pro inside ubuntu).**

Is there something i can use to do this and how would it be used.

I strongly recommend G4L. Free, effective, updated often.

[http://sourceforge.net/projects/g4l]("http://sourceforge.net/projects/g4l")

You create a boot CD by burning the ISO image, boot it, and go through the menus. You can image disk-to-disk or over a network disk-to-FTP and then boot on an identical machine and image FTP-to-disk.

-HF

---

### Post by evilbuntu on 2009-01-14
I am downloading this ISO right now. do you know if this will recognize USB drives as well.

I am now looking for something that will make an ISO clone and save it on an external USB drive. otherwise i can try it when i get home.

thanks

---

### Post by hangfire on 2009-01-14
> **evilbuntu said:**
> I am downloading this ISO right now. do you know if this will recognize USB drives as well.

If you are speaking of G4L, I have had good luck imaging to and from USB drives, including thumb drives and USB/Sata and USB/IDE adapters.

You have to be careful what you want- it will reimage the USB drive, if that is what you specify. In FTP mode, the default is to save to a compressed filename that you set (as long as you have a dir named *img* under the FTP home directory).

I'm pretty sure you can do drive-to-(USB)drive to a file name, but I don't have a system to boot it on at the moment.

-HF

---

### Post by evilbuntu on 2009-01-15
> **hangfire said:**
> If you are speaking of G4L, I have had good luck imaging to and from USB drives, including thumb drives and USB/Sata and USB/IDE adapters.

You have to be careful what you want- it will reimage the USB drive, if that is what you specify. In FTP mode, the default is to save to a compressed filename that you set (as long as you have a dir named *img* under the FTP home directory).

I'm pretty sure you can do drive-to-(USB)drive to a file name, but I don't have a system to boot it on at the moment.

-HF


i found the g4l but it did not want to cooperate with my machine for some reason

---

### Post by hangfire on 2009-01-20
> **evilbuntu said:**
> i found the g4l but it did not want to cooperate with my machine for some reason

Please tell us what went wrong, maybe we can get through it.

G4L has many boot options to get through boot and/or recognize different hardware. Did you get the boot menu? Did you try the different kernels?

-HF

---

### Post by Slim Odds on 2009-01-20
I use Clonezilla to backup to an external USB drive.

---

### Post by Psychaotix on 2011-07-11
Hey all.

I did a quick search on how to image a harddrive under Ubuntu on Google, and this is the first one that came up. for reference, Im using a LiveCD of ubuntu 11.04 on a Sony Vaio PCG-K76P, and Im unable to install it on the computer since I'm not allowed to do that.

The computer has recently decided to go Down, and crash in a bad way, so I was hoping there was a way I could recover the files that are needed by the people im helping and put them onto a disk image that I could later read on another computer. Does anyone have any suggestions?

Thanks
Psychaotix

---

