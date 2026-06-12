---
title: "Simple Issue - How to COMPLETELY COPY Ubuntu from one HDD to another"
date: 2006-07-26
forum: Desktop Environments
---

### Post by jackkerouac on 2006-07-26
Okay, here's the situation.

My system is dual boot, with Windows XP on one hard drive (hda) and Ubuntu on another (hdb).

I have a new, larger, faster hard drive that I want to put Ubuntu on. I am going to remove the Windows hard drive and replace it with the new one and then copy everything over. I still want Grub to work.

So, in a nutshell, I want to copy everything from hdb to hda, including Grub so that when I turn my system on again, it looks as if nothing has happened except it has more space.

Any ideas? Thanks!

---

### Post by Ziox on 2006-07-26
i would first format the new partition, then mount it using the mount command, and then just copy everything over...(i suggest mounting the new volume as the same mount point as the partition before)..as for GRUB, you can run the command grub, then setup <TAB> and then install <TAB>...i'll find a better thread....

But that's how I would do it, but i might not be the best way...and i think you're better waiting for more replies...(many will be better than mine)

---

### Post by ajgreeny on 2006-07-26
Partimage should be the answer, but you will have to run it from a live CD session, as you can not make a disk image of a mounted partition.  I don't know if the live CD of ubuntu has it on but if not, Knoppix certainly does, so get a copy of that.  

Run partimage and make a disk image of your current ubuntu partition.  Then run it a second time and copy the disk image you just made to the new disk, (you may need to format it ext3 first, but I can't remember if that is needed or is part of the write process).  Your grub menu.lst may point to the wrong partition after doing all this so bear in mind that you will either need to remove your old disk so the new one takes it's place, or edit the list to take account of the change.

Good luck!

---

### Post by jackkerouac on 2006-07-26
I'm going to call that Plan B (mostly because it sounds fairly complicated).

Any other suggestions?

---

### Post by endfx on 2006-07-26
Sorry jack,

but it sounds like ajgreeny has exactly what you want.
You want to create an image you the partition with ubuntu on it
and then copy that image onto the partition on your new harddrive.

It sounds complicated (and it is, the first time you do it) but this is really the best way to get an exact copy of it.

The other thing you could do is use 2 harddrives: Windows on your new harddrive and ubuntu on the old harddrive. Now you could make a big partition on your new drive that you can access from ubuntu. You would just have to modify grub a little bit so you can boot off of 2 hard drives (this is really easy to do)

---

### Post by carontis on 2006-07-26
Well, for some thing similar but not the same I did an ISO image, and only after writing it to the new hdd so you will not loose some part; I think also it should copy the exact partioning so you should find the new hdd ready. Remember: I've never tried from hdd to hdd so I don't know if it really can work, but I would try in this way.

---

### Post by jackkerouac on 2006-07-26
> but it sounds like ajgreeny has exactly what you want.
You want to create an image you the partition with ubuntu on it
and then copy that image onto the partition on your new harddrive.

I agree, but I wanted to avoid using Knoppix or some other live CD distro to do it.

Is there no way for me to install the first hard drive as hda, mount it, then copy everything over directly from inside Ubuntu? Is there a way to configure cp to do it?

**UPDATE:** What if I installed the new hard drive as hda, the used gparted to partition it and then used

```

rsync -a /dev/hdb /dev/hda

```

or perhaps (mounted first)

```

dd if=/dev/hdb of=/dev/hda

```

Would that work?

---

### Post by jackkerouac on 2006-07-26
Okay, this is the plan, can someone let me know if it is going to work?

[LIST=1]
[*] I take out the Windows drive (hda) and put in the blank one.
[*] I use Gparted to create ext3 file system and swap partition.
[*] I issue the following commands:

```

sudo mkdir /mnt/hdb_Ubuntu 
sudo mkdir /mnt/hda_Ubuntu 

sudo mount /dev/hdb /mnt/hdb_Ubuntu 
sudo mount /dev/hda /mnt/hda_Ubuntu 

sudo cp -ax /mnt/hdb_Ubuntu/. /mnt/hda_Ubuntu/. 

gksudo gedit /mnt/hda_Ubuntu/etc/fstab *# to make sure everything is correct*
gksudo gedit /mnt/hdb_Ubuntu/boot/grub/menu.lst *# hopefully I won't need to mess with this*

```
[*] Now I disconnect the new Ubuntu drive (hda) and re-connect the Windows drive (hda).
[*] I disconnect my original Ubuntu drive (hdb) and connect the new drive (hdb).
[*] I discard the old Ubuntu drive.
[*] I laugh and sing as everything works perfectly and I never have any problems ever again.
[/LIST]

---

### Post by Ziox on 2006-07-26
> **jackkerouac said:**
> Okay, this is the plan, can someone let me know if it is going to work?

[LIST=1]
[*] I take out the Windows drive (hda) and put in the blank one.
[*] I use Gparted to create ext3 file system and swap partition.
[*] I issue the following commands:

```

sudo mkdir /mnt/hdb_Ubuntu 
sudo mkdir /mnt/hda_Ubuntu 

sudo mount /dev/hdb /mnt/hdb_Ubuntu 
sudo mount /dev/hda /mnt/hda_Ubuntu 

sudo cp -ax /mnt/hdb_Ubuntu/. /mnt/hda_Ubuntu/. 

gksudo gedit /mnt/hda_Ubuntu/etc/fstab *# to make sure everything is correct*
gksudo gedit /mnt/hdb_Ubuntu/boot/grub/menu.lst *# hopefully I won't need to mess with this*

```
[*] Now I disconnect the new Ubuntu drive (hda) and re-connect the Windows drive (hda).
[*] I disconnect my original Ubuntu drive (hdb) and connect the new drive (hdb).
[*] I discard the old Ubuntu drive.
[*] I laugh and sing as everything works perfectly and I never have any problems ever again.
[/LIST]

so your main system won't be mounted at "/"? well, that could be a problem, because lots of programs refers to other files, and usually their path begins w/ "/"...but it might work...

---

### Post by jackkerouac on 2006-07-27
> so your main system won't be mounted at "/"? well, that could be a problem, because lots of programs refers to other files, and usually their path begins w/ "/"...but it might work...

I'm confused. I want the new drive to be EXACTLY the same as the old one - no differences, all links the same, etc., etc.

What cp commands do I need to make that happen? Did I screw up the proposed command structure?

---

### Post by Ziox on 2006-07-27
> **jackkerouac said:**
> I'm confused. I want the new drive to be EXACTLY the same as the old one - no differences, all links the same, etc., etc.

What cp commands do I need to make that happen? Did I screw up the proposed command structure?

i'm just confused about these commands:

sudo mkdir /mnt/hdb_Ubuntu 
sudo mkdir /mnt/hda_Ubuntu 

sudo mount /dev/hdb /mnt/hdb_Ubuntu 
sudo mount /dev/hda /mnt/hda_Ubuntu 

it seems like you are copying from one folder to another, and that those folders have different names...(also it was my fault for the previous post, i naturally assumed that your system is mount in the folder "/" which now I realized doesn't apply to everyone...)

---

### Post by sharperguy on 2006-07-27
looks like he's just mounting them there temporarily to copy them.

You'll need to mess with grub and fstab.

---

### Post by Ziox on 2006-07-27
> **sharperguy said:**
> looks like he's just mounting them there temporarily to copy them.

You'll need to mess with grub and fstab.

ok, thanks for clearing that up...i thought about it after I wrote my post...and noticed that...

---

### Post by jackkerouac on 2006-07-27
I have decided to use [Ghost 4 Linux (g4l)]("http://freshmeat.net/projects/g4l/") to copy the drive. The 'Click & Clone' option is pretty simple, so I will let you folks know if it works as advertised.

If so, it would make it very easy to clone one drive to another.

**UPDATE:** Okay, it's done. Here's how I did it, so perhaps others wanting to can as well.

First, I went and got a copy of [Ghost 4 Linux (g4l)]("http://freshmeat.net/projects/g4l/"). I then went and got a copy of Gprted and burned them both to CDs.


I booted up with g4l. I used the **Click to Clone** option and selected copying the entire hdb to hda. It copied it successfully, bit by bit. **THIS IS VERY SLOW**, so be ready for that (*it took me 10 hours*).

I then rebooted with gparted. Since I was copying a 40 GB drive to a 250 GB drive, the partitions were screwed up. I deleted the extended and linux swap partitions, extended the ext3 partition to take up 245 GBs of the drive and then created a new extended and linux-swap partition.

Voila! Cloned drive.

Let me know if you have any problems. Thanks for the help!

---

### Post by leona on 2006-11-14
Well I went down the G4L route as well, though it seems to have cloned my windows parts, (I'll have to double check that) ok, cos I could boot windows, it seems to have screwed my Linux partitions, I have NO mount points, how do I fix this?

arr, hang on, maybe a bit of background might help, I've replaced a IDE drive with an SATA drive, noticed that the drive is now refered to as sda not hda, so this is probably why things don't work, what do I need to edit to fix this?

---

