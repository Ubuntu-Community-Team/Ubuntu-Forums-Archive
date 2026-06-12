---
title: "How to move / from one hard drive to another"
date: 2006-09-23
forum: Desktop Environments
---

### Post by jonread1983 on 2006-09-23
Hey all :D

When i installed ubuntu i installed / onto a 5GB partition. Ive found out this wasnt enough though, and have managed to get it to 95% full already (a months use???)

Question, how possible is it to move / to another hard drive?

I ran a quick theck for other posts and they seem to instruct how to move /home. Im after moving /

Cheers for any help guys, although ive binned Windows once and for all, im still a bit of a noob. :(

---

### Post by alecjw on 2006-09-23
Just grow your 5GB partiton uisng gparted on the livecd/dvd

---

### Post by jonread1983 on 2006-09-23
can I still do this if the whole drive is taken up? I have / swap and /home, will increasing / reduce /home and shift along swap?

---

### Post by kidders on 2006-09-23
Hi there,

All you need to do is copy your / someplace else, update your bootloader, etc. and reboot. Here's a rough step-by-step...

[LIST=1]
[*]Shut down your graphical environment, as well as all the applications, services and other running processes you can.
[*]Check **ps aux** and **lsof** to make sure they're both very small lists. This ensures that no files will be altered *during* the copy (which may take some time), resulting in an inconsistent filesystem.
[*]If you haven't already done so, create a new partition for your / (perhaps with cfdisk or a similar tool). Format it with one of the "mkfs" tools.
[*]Mount your destination filesystem someplace, with a **mount /dev/sdc1 /mnt/newubuntu** for example.
[*]Begin the copy and go have a coffee! This has to be done carefully, to preserve special filesystem features, such as symlinks and permissions. **cp -dpR / /mnt/newubuntu** maybe. *DO NOT* try to "mv" your root filesystem.
[*]Revise your new /etc/fstab to reflect the change ... update any references to your original root filesystem location. I'm assuming here that you're not using software RAID, transparent filesystem encryption, etc., that would also need to be tweaked.
[*]Update your Grub. If your new / is on a new physical device, you may wish to reinstall Grub completely, so you could remove the original hard drive altogether.
[*]Shut down and reboot.
[*]Once your system boots, satisfy yourself that you are, in fact, booted into the "new" environment, and not the "old" one. For security, double-check the permissions of your filesystem root with **ls -ld /** If in doubt, do a **chown root:root / && chmod 755 /**
[/LIST]

Now you should be done. Off the top of my head, I can't think of anything else you would need to do, but if there's something specific that concerns you, post back and I'll try to help.

---

### Post by kidders on 2006-09-23
Oops... missed the boat with this one. If your can at all, resizing your root takes far less time... try that first!

---

### Post by CatKiller on 2006-09-23
> **jonread1983 said:**
> Hey all :D

When i installed ubuntu i installed / onto a 5GB partition. Ive found out this wasnt enough though, and have managed to get it to 95% full already (a months use???)

Question, how possible is it to move / to another hard drive?

I ran a quick theck for other posts and they seem to instruct how to move /home. Im after moving /

Cheers for any help guys, although ive binned Windows once and for all, im still a bit of a noob. :(

I think it's quite easy. Put the new hard drive in, boot from the Live cd, run GPartEd, copy the existing partition to the new drive, resize the partition on the new drive. The procedure then varies depending on what you want to do next - just have the new drive in, have both in, new drive as master or slave, and so on. But you'll probably have to mount the new partition in the Live cd environments and edit the configurations of Grub and FSTab to reflect the changes that you've made to the filesystem.

---

### Post by jonread1983 on 2006-09-23
ok thanks guys i'll give it a bash, but im not too good with terminal and commands yet. But i'll try :)

Another thought i had was to install Ubuntu freshly onto a new drive. If i were to do this, what is the equivalent of windows "documents and settings"? Are they hidden files in /home?

If i were to install to a new drive, which folders would i need to copy, and the most important question:

Where is the cache of the files i downloaded through SPM? I think I could copy these to a new folder, add this folder as a "repository" and install them back on? Save me having to download them all again? Or am i mistaken?

---

### Post by kidders on 2006-09-24
There are HOWTOs for backing up your package cache around here someplace ... If I could only find one!

---

### Post by CatKiller on 2006-09-24
Actually, I just did this, and GPartEd didn't seem to want to make a Primary partition that would boot. Could well have been something that I did, though. Anyway, in the end I did a dd from the smaller drive to the larger drive with ```
dd if=/dev/hda of=/dev/hdb
``` and then used GPartEd to resize the / partition, and that worked a treat.

---

