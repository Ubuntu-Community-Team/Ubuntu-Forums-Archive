---
title: "Dual-booting and Partitioning"
date: 2008-05-21
forum: Desktop Environments
---

### Post by decatur-linux on 2008-05-21
I have Ubuntu 8.04 installed and working on a 320Gb SATA disk.  I want to dual-boot Kubuntu 7.04.  Hardy Heron is taking up about 30Gb and I want to install Feisty Fawn on the same size partition.

I have installed an extended partition for Feisty Fawn to go into.

When I load the live-CD of Kubuntu and try to install it, I choose "Manual" partition, since "Guided" only gives me the choice of "entire disk" or "largest unused space", and I want to limit the size of the Kubuntu installation.

When I manually set up the partition for Kubuntu I tell it that the mount point is "/", but shows me that the corresponding partitions for Ubuntu are to be mounted at "media/sda2" and "media/sda3"; these are the "boot" and "home" partitions for Ubuntu.  Is that what I want?

If I change the mount point for sda2 and sda3 to '/' and "/home" respectively, it fusses about there being TWO partitions that have "/" as a mount point.  As far as I can tell, it know nothing about dual-booting.

So I end up abandoning the install.

Some help, please.  Thanks.

---

### Post by SgtDude on 2008-05-21
> When I manually set up the partition for Kubuntu I tell it that the mount point is "/", but shows me that the corresponding partitions for Ubuntu are to be mounted at "media/sda2" and "media/sda3"; these are the "boot" and "home" partitions for Ubuntu. Is that what I want?

If I change the mount point for sda2 and sda3 to '/' and "/home" respectively, it fusses about there being TWO partitions that have "/" as a mount point. As far as I can tell, it know nothing about dual-booting.

You're a little inconsistent in your post.  In the first paragraph you say that sda2 is your /boot partition, but in the second paragraph you say sda2 is your / partition.  Could you please clear this up?

In any case, you shouldn't have any major issues using the same partition for the /home mountpoint on both installs, but you will most definitely have issues using the same partition for your / mountpoint on both.  I'm not sure about /boot, I've never tried using the same partition for 2 installs before.

Anyway, if you could describe the complete layout of your HD, that would be helpful.  (i.e. sda1 - windows, sda2 - ubuntu /, sda3 - shared /home, sda4 - kubuntu /)

---

### Post by decatur-linux on 2008-05-21
Let me clarify my original post:

When I run GParted on my original Ubuntu 8.04 installation it shows this:
**Partition---Filesystem---Mount Point**
/dev/sda2---------ext3---------------/    
/dev/sda3---------ext3---------------/home
/dev/sda4---------linux-swap
/dev/sda1---------extended

When I boot the Kubuntu live-CD and start to partition my 30Gb partition within the extended partition it shows this:
**Partition---Filesystem---Mount Point**
/dev/sda2---------ext3---------------/media/sda2
/dev/sda3---------ext3---------------/media/sda3
/dev/sda4---------linux-swap
/dev/sda1---------extended
.
.
.
I can understand mounting my /dev/sda3 at /media/sda3, but why mount my boot partition of Ubuntu at all?  I realize that the /media/sdax is in relation to my new root [/] in Kubuntu, but it seems strange to me, and I don't want to lose my Ubuntu installation, so I abandon the Kubuntu install.

Thanks for your reply.

---

### Post by webarchitect on 2008-05-21
Well that is really interesting...I haven't tried dual booting before. I have been mainly running my other OS's and modules via virtual systems. 

Although if I were you, I'd get another HD and try it out...I mean experiment on it. 

I'm interested to know how this is going to be done. I'm gonna be tuned in to the replies.

---

### Post by Silby on 2008-05-22
Hi,

When you run the feisty installer and get to the partitioning, the system will look for existing partitions and automaticly assign 'mount points' to them.

In this case, feisty finds several partitions:
/dev/sda2 -> your hardy root partition, you do NOT want to install kubuntu there because obviously it will overwrite your hardy install. The partitioner wants to mount this particular partition under Kubuntu feisty under the /media/sda2 partition. This means that if you install kubuntu and go to the /media/sda2 'folder', you would see your ubuntu hardy root partition.

/dev/sda3 -> your hardy home partition. Here, the partitioner wants to mount this under Kubuntu as /media/sda3, meaning that if you were to install kubuntu and go to /media/sda3, you would see your ubuntu hardy home folders. Now here you CAN chose to mount this partition under Kubuntu too as /home, however as this is your first dual boot experiment, i wouldn't do that just yet.

Your swap partition can be used by both ubuntu and kubuntu as the same partition. Unless you want to virtualize one of both in the future and run them simultaniously. If you want to do this, create an extra partition for the kubuntu swap. Chose to not use this ubuntu swap partition and use the kubuntu swap partition as swap.

Install kubuntu root '/' to /dev/sda1. If you want a seperate /home partition, make it first. Else if you only chose a / partition, everything will be mounted under that one mount point.


This is all because linux offers you to install data on separate partitions (and as such even different drives). Debian (and Ubuntu) has a specific, fixed folder structure on which it is built. Several of those are:
  / 
  /boot
  /home
  /lib
  /var
  etc
Each of these have a specific function and they can all be on one, or more partitions. You separated / and /home on your ubuntu install. This means that /, /boot, /lib, ... are all located on the /dev/sda2 partition, and your /home folder is located on the /dev/sda3 partition. If you were to format /dev/sda2 and install a new OS there, you would still have /dev/sda3 with your home data on it.

So in short: Kubuntu just wants to mount the partitions so you have access to them. If you chose to install Kubuntu to /dev/sda1, set your / mountpoint to that partition. Your hardy install and data will stay in tact and be completely separate from your feisty install.

---

### Post by SgtDude on 2008-05-30
> **decatur-linux said:**
> Let me clarify my original post:

When I run GParted on my original Ubuntu 8.04 installation it shows this:
**Partition---Filesystem---Mount Point**
/dev/sda2---------ext3---------------/    
/dev/sda3---------ext3---------------/home
/dev/sda4---------linux-swap
/dev/sda1---------extended

When I boot the Kubuntu live-CD and start to partition my 30Gb partition within the extended partition it shows this:
**Partition---Filesystem---Mount Point**
/dev/sda2---------ext3---------------/media/sda2
/dev/sda3---------ext3---------------/media/sda3
/dev/sda4---------linux-swap
/dev/sda1---------extended
.
.
.
I can understand mounting my /dev/sda3 at /media/sda3, but why mount my boot partition of Ubuntu at all?  I realize that the /media/sdax is in relation to my new root [/] in Kubuntu, but it seems strange to me, and I don't want to lose my Ubuntu installation, so I abandon the Kubuntu install.

Thanks for your reply.

I see your concern now.

When the Kubuntu installer mounts /dev/sda2 on the folder /media/sda2, it's not planning on writing anything to /dev/sda2, only making it accessible from within the new installation.  If you're /home partition is separate, you probably won't need this and can either leave it there (it won't hurt anything) or tell the installer not to mount it at all (I'm not sure off of the top of my head how to do this, but I think you either clear out the mountpoint (in this case "/media/sda2") or change the "use as" to "do not use" or something like that).  In any case, if you're installing onto a different partition (i.e. /dev/sda1), then you have nothing to worry about.  The installer won't change /dev/sda2, it'll only mount it.  This is because Kubuntu won't actually install anything into any folder under /media.  The /media folder's purpose is to give other filesystems (usb media, DVD-ROM drives, network shares) a logical place in the filesystem to mount.  The OS itself doesn't make changes to the filesystems mounted under /media without explicit user interaction.

Sorry for the late response.  Hopefully Silby's post answered your questions.  I just figured I'd put my 2 cents in too.

---

