---
title: "Re-install from second hard disk"
date: 2006-04-26
forum: Desktop Environments
---

### Post by madsmaddad on 2006-04-26
Hi, I need help. I want to be able to re-install Ubuntu for my classes, I have Workstations with two hard disks, the second hard disk partitioned into two Dos disks, One has the Ghost images for NT4 Workstation and server, the second currently has Mandrake files and we have a CD that partimages the Mandrake down to the first hard disk if we need a linux setup. The  guys who created this for me left out a lot of the install so it dosn't work too cleverly. I want to copy  all the Ubuntu files to that second hard disk, and have a way of 'ghosting/installing' it down to the first disk.

Can Anyone give me any guidance on how to do this, and which files/directories I do not need for this install. I would also like to tailor it so that it does not prompt for country/keyboard, and also possible have a set username. This should make the install quicker. 

I am a relative newbie to linux, after using unix variants years ago - Xenix?

Thanks,

---

### Post by louis_nichols on 2006-04-26
Hi! yours doesn't sound like a difficult issue, it's just that I didn't really understand what you need to do. :)

I think this sentence is the key:
> I want to copy all the Ubuntu files to that second hard disk, and have a way of 'ghosting/installing' it down to the first disk.


What I don't understand is what prevents you from simply installing Ubuntu *down to the first disk*, where you need it.

---

### Post by madsmaddad on 2006-04-26
Ghosting down NT server takes 5 mins, NT wkstn about 7, Doing it with Mandrake about 15, and Installing Ubuntu from the CD about an hour and a half, and has to be watched to input parameters. 

I don't need  it all, such as the docs, and installing from the seconf HD should be faster. In a lab period of 2 hours, a faster install is needed. 

Thanks.

---

### Post by louis_nichols on 2006-04-27
I think I understand now. You have several OS's for different people and need a faster way to "install" the OS you need yourself, which would be Ubuntu. Why don't you use norton ghost or partimage (which, by the way, is amazing in terms of data compression)?


Another thing I can think of is [here]("https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29"), but for this you need a liveCD that will give you the tar command to restore. The advantage of it is that you can actually choose parts to exclude. 
As for leaving out the docs... I think there is an option when installing debs that will not install man pages and documentation, but I'm not sure. I know rpm has such an option.

---

### Post by madsmaddad on 2006-04-27
OK, Looks good. I  hope the tar image isn't too big for th storage partition. Then I guess I'll see if I can build a boot floppy that will extract the system to the hard disk and recover Grub. 

Something else I was reading elsewhere suggested I use a Bootable CDROM system to create the tar. 

Only one way to find out I guess...

Thanks for your help.

---

### Post by louis_nichols on 2006-04-27
oh, yeah... forgot about the grub... I think the liveCD option  is better. It spares you the trouble of making a bootable floppy complete with tar. Perhaps you could make a bash script that will easily restore grub after un-tar-ing the backup, which is definitelly more do-able with a liveCD... just a suggestion.

as for size, you needn't worry! I had a more than 3GB install, which compressed to little more than 1.5 GB.

Oh! I just realized smth! Make a small partition (up to 100MB) that contains a typical boot folder. In it, for menu.lst you can write a configuration to boot any of the OS's that could lie on the first partition. then it'll just be a matter of choosing the current OS from the menu.

---

### Post by madsmaddad on 2008-05-02
It's been a while, But I discovered Clonezilla. 

The configuration is now quite weird- The second hard disk is partitioned as a 4G extended partition containing two 2G logical FAT partitions. These hold the ghost program and images for the NT wkstn/server. The rest of the second disk is an Ext3 partition. I Installed Ubuntu on the first hard disk, and then used Clonezilla to image it up to that ext3 partition on the second hard disk. I can now use Clonezilla to bring it down whenever I need it. I could also stick XP up there if I wanted to. 

Part of the reasoning behind what I have had to do is that if I use a different partitioning arrangement, then NT changes the drive letters and doesn't work properly. The new partition on the second hard disk had to be something that NT didn't recognize. 

So Job done, thread closed. Thanks for your help.

---

