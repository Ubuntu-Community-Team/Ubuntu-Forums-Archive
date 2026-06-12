---
title: "how to proceed after successfully mounting /dev/sda3 in ubuntu -fixing os won't mount"
date: 2011-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by taoist33 on 2011-05-26
Hi, been working on this for awhile and have made progress where I can mount a win7 partition after editing fstab , but in order to mount it I have to use the sudo command from terminal otherwise it won't mount.  My goal is to retrieve my win7 partition and get it to boot again. I am dual booting with 10.10 on a dell 8100 studio machine. I don't know what the next steps would be after being able to successfully mounting it to get it to boot up.
  I got it finally to mount after installing the ntfs-3g.

 I would greatly appreciate the help thanks

I am using a single sata HD 1.5 terabyte with dual boot 10.10 & win7.

here is the error if I just try to mount it in "places" Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda3 on /media/Win7

can mount it in terminal using sudo command

---

### Post by sanguinoso on 2011-05-26
I'm confused. Do you mean you cannot boot to Windows 7 or you're having problems reading the data from your windows partition in Ubuntu?

---

### Post by taoist33 on 2011-05-26
Wow thanks for the quick reply, I can't boot into windows and in ubuntu I  get the error message when trying to mount the windows OS partition, I did a reinstall clean and stored my ubuntu files on the windows partition data wise could see data and files okay , but pulled a flash drive out of ubuntu with out safely ejecting it and thats what seemed to start this trouble.

---

### Post by sanguinoso on 2011-05-26
What error does it give you when trying to boot into Windows? Have you tried mounting with sudo or does it give you an error?

---

### Post by taoist33 on 2011-05-26
I wish it gave me an error lol, it actually hangs a second and than reboots the computer. black screen type.  

sequence,
1 select win7 os from grub upon boot up

2 machine hangs black screen no data

3 computer reboots after a second or 2

---

### Post by taoist33 on 2011-05-26
using the sudo command I can finally mount the /dev/sda3 which is 

the win7 installation however, however need to know what to do 

next to make it bootable again

---

### Post by taoist33 on 2011-06-01
Well since no one else wanted to take up the gauntlet I will mark this one as closed myself.  I found out that the MBR for the windows partition was blown out .  
fix the MBR
after creating a usb bootable for win7
boot and choose command prompt , then at the command prompt type
bootrec /Rebuild BCD
bootrec /FixMbr
bootrec /FixBoot

after doing this it re-enables the recovery partition. Now the next wonderful ephipany.  The backup restoration disks for the Dell xps 8100 studio are not created for a 1.5 tera byte drive so it hangs at 35 % when formatting the drive. Than it pops up with an error 
0x4001100200001005 which means that it is a media error since the restoration disk software was not created to work on large 1.5 terrabyte drives.   Called Dell and they are going to send me out the proper set of Restorations discs under warranty. Be here in a couple of days. Learned alot through this experience. Maybe it will help someone else. 

In closing here is an excellent article 
[http://essayboard.com/2010/12/19/adding-new-hard-drive-onto-ubuntu-10-10](http://essayboard.com/2010/12/19/adding-new-hard-drive-onto-ubuntu-10-10)

---

