---
title: "Grub Error 17, cannot access hard disk"
date: 2006-02-17
forum: Desktop Environments
---

### Post by thumbsoup on 2006-02-17
I messed up my Ubuntu installation, and I do not know how to fix it.  I think it is because I made a bad change to menu.lst, but it might be something wrong with the MBR.

"Grub loading, please wait...
Error 17"

Can I use the Live CD to access hda1, so I can edit menu-lst and undo this problem?  I did save a backup copy of the file, but how do I get to it?  

Or if I have screwed up my MBR, how do I tell?

I can see all the partitions in GParted from the Ubuntu Breezy Live CD.  Ubuntu is on hda1, Kanotix hda2.  Spare partition on hda3 just to store data.  While in the Live CD, I cannot see the hard drive in Device Manager.

I changed the menu.lst so that Grub would give me the option of booting into Kanotix.  I had done this before, but at some point in the last couple weeks Grub lost that section of menu.lst. 

1) Maybe I messed up my menu.lst:
I also added a couple lines to the first Ubuntu boot option (newest kernal) regarding hiding the Kanotix partition and unhiding the hda3 partition. My guess is that is where the problem is, but I don't know.

2) Or I messed up my MBR while in Kanotix:
I tried to ap-get update && apt-get distupgrade in Kanotix, which didn't work (GPG key issue).  I looked thru their forum and saw notes  saying don't try this while X is running, it might screw up your machine.  Oops.  Didn't notice any problems until I rebooted. 

Need help, I am completely stuck!  

Thanks.

---

### Post by thumbsoup on 2006-02-18
I booted from a CD the latest version of SystemRescue.

1) SystemRescue found my hard drive, and using the following boot options allowed me command line access to my Ubuntu hda1 partition:

fb1024 nokeymap root=/dev/hda1

When I login to Ubuntu, X fails to load:

"Fatal: could not load /lib/modules/2.6.15.1-fd18/modules.dep"

2) I backed up my current Grub menu.lst, and then using nano editor, removed the hide/unhide options from Ubuntu and Kanotix sections.  Also removed "savedefault" line from Kanotix section, just due to superstition.

Rebooted.  Still get Grub "Error 17"

3) Booted back into SystemRescue CD, and ran Qtparted.  Noticed that the Kanotix partition hda2 was the only partition set to "Active".  Made sure that hda was not mounted, and switched the Active partition to hda1.

Rebooted. Still get Grub "Error 17"


Any ideas why I am still getting this error?

---

### Post by lha on 2006-02-18
From [grub manual:]("http://www.gnu.org/software/grub/manual/grub.html")

[Error] **17** : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Command: **hide** *partition*
    Hide the partition partition by setting the hidden bit in its partition type code. This is useful only when booting DOS or Windows and multiple primary FAT partitions exist in one disk

My guess is you damaged your partition table with 'hide'. Hide changes the partition type label from fat to hidden fat. I don't know what hide does to other partitions, but it looks like it didn't do any good...

Can you post the output of
```
sudo fdisk -l
```? It'd show if your partition labels are warped.

---

### Post by thumbsoup on 2006-02-18
I can't post the output, as I can't copy from that machine to this one.  Booted from Ubuntu Live CD to check this. 

fdisk -l  

does find all my partitions, and hda1 (Ubuntu) is flagged as the Boot partition.

However the file system is shown as "Amoeba", same as hda2 (Kanotix). Hda1 should be ext3, and I think hda2 should be ext3 too.

Checked this in GParted from Live CD, and that showed "Amoeba" as well.

*********************
I did try the instructions below from a different thread to restore Grub on the MBR, but it didn't work.  When I tried the grub-install step 7, I got an error:

"unable to lookup ubuntu via gethostname()

I will reboot with SystemRescue later and see what it says about the partitions.
******************************
Originally Posted by ghostintheshell
Aaargh!! Thank you guys!! Very very very much!! You saved my virtual life!

I lost my Grub / MBR and YOU restored it!

After searching too much time on the web, I fell on this topic. I read it completely and applied a mix of your solutions.

Here's the steps I followed to restore GRUB / my initial MBR:

1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> fdisk -l (Mine is /dev/hda4)
5. Mount the root partition of Ubuntu -> mount -t ext3 /dev/hda4 /mnt/ubuntu (replace /dev/hda4 by your Ubuntu partition determined at the step 4)
6. Chroot the mounted partition -> chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> grub-install /dev/hda
8. Exit the shell
9. Reboot

---

### Post by lha on 2006-02-18
[QUOTE=thumbsoup]I can't post the output, as I can't copy from that machine to this one.  Booted from Ubuntu Live CD to check this. 

fdisk -l  

does find all my partitions, and hda1 (Ubuntu) is flagged as the Boot partition.

However the file system is shown as "Amoeba", same as hda2 (Kanotix). Hda1 should be ext3, and I think hda2 should be ext3 too.

Checked this in GParted from Live CD, and that showed "Amoeba" as well.

*********************
I did try the instructions below from a different thread to restore Grub on the MBR, but it didn't work.  When I tried the grub-install step 7, I got an error:

"unable to lookup ubuntu via gethostname()

I will reboot with SystemRescue later and see what it says about the partitions.
[/QUOTE]

Ok, looks like that hide-thing messed up your partition table. I believe grub has no part on this one, it just doesn't know how to mount your partitions because they have wrong labels. I'd try to change the partition labels to 83 (linux) and see if it helps. Of course, backup up the things you can't afford to lose. Also, backup of your partition table is a good idea.

---

### Post by thumbsoup on 2006-02-18
When I booted back into SystemRescue CD, Qtparted correctly shows my hard drive partitions for hda1 thru hda4 (swap).  

Is there a way to repair a partition table without destroying my current Ubuntu install?

---

### Post by lha on 2006-02-19
[QUOTE=thumbsoup]Is there a way to repair a partition table without destroying my current Ubuntu install?[/QUOTE]

You can use fdisk to change partition labels. Start fdisk
```
sudo fdisk /dev/hda
```
and use
```
t <enter>
*partition_number* <enter>
83 <enter>
```
to change partition label to 83 (Linux) for partition hda*partition_number*

This is quite safe to do, I have done it many times without problems. I still encourage you to make backups of files you cannot afford to lose. Something can go wrong, and it is a pain to lose valuable data...

---

