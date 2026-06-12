---
title: "How to auto mount NTFS partition at startup?"
date: 2008-06-06
forum: Desktop Environments
---

### Post by dcharry on 2008-06-06
Hello everyone, 
      I have the latest Ubuntu installed on my pc and I just wonder is there a way to mount my other windows partition automatically at Ubuntu startup, I saved my music on those partitions and everytime when I opened up Amarok all musics won't be read until I mounted those disks first.

Many thanks in advance!

Harry

---

### Post by krishnakittu on 2008-06-06
which version of ubuntu ur using now.
in 8.04 they r automatically mounted on the startup.

---

### Post by xaco1234 on 2008-06-06
actually that's not true 8.04 don't auto mount as standard.

---

### Post by dcharry on 2008-06-06
> **krishnakittu said:**
> which version of ubuntu ur using now.
in 8.04 they r automatically mounted on the startup.

I'm using 8.04 but its not mounted automatically on the startup at all, kinda curious why here!:)

---

### Post by Nythain on 2008-06-06
so, im not gonna debate wether or not somethign should be doing something its clearly not, because thats sort of moot... but im also not gonna retype something thats been typed a billion times...

search google or teh forums for
"automount ntfs fstab"

will bring up tons of results, in a nutshell all you really have to do is edit one file and tell it what partition to mount, where to mount it, what filesystem that partition is and any other options it should use during the mount in a line similar to be not exactly like this...

/dev/hda3   /path/to/where/to/mount/it     ntfs(or ntfs3-g)    defaults    0   0

you get the point

---

### Post by crasher35 on 2008-12-25
I am having the same problem, however, I looked up how to automount an NTFS partition on google, followed the directions but it doesn't work.

This is what Fstab currently looks like for me.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1	UUID=9CEC91AAEC917EE8	ntfs-3g	defaults	0	0
# /dev/sda5
UUID=70b75f46-b272-42a6-a4a5-8ccc5d155231 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=14a83cc6-78c3-4cd2-909d-c5450a6edcaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The partition I'm trying to get to automount is:

```
# /dev/sda1	UUID=9CEC91AAEC917EE8	ntfs-3g	defaults	0	0
```

Now I've tried a lot of different things.  I've tried using "/media/XP" instead of the UUID.  I've tried having it do username and password and a few other commands.  None of them work.  I just don't understand why it won't automount at startup when I've pretty much followed the directions to a tee.

Heck, I've even tried removing the "#" at the beginning of the line.  All that does is make it so that I can't even see that the partition is there at all.

Please help me figure this out.

Oh one last detail... I'm running Intrepid Ibex.

---

### Post by crasher35 on 2009-01-02
Okay!  I understand now.  The # signs in my fstab file were in fact commenting out the code like I thought it was (I wasn't sure, I thought it might indicate a new line).  So I put in the information that I should have and that made the partition disappear completely (not showing up under "Places").

What I didn't realize that I had to do was that I had to make the directory in /media.

So, what you need to do is that you need to edit fstab

```
sudo gedit /etc/fstab
```
(Run this in terminal).

and tell it what partition to mount, where it's going to mount it, and the filesystem it's using (ext3, ntfs, fat32, etc).

For example:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/XP       ntfs-3g defaults        0       0

```

(To find info on your partition, just go into terminal and type *sudo blkid*.  You also want to use ntfs-3g for the type instead of just ntfs to be able to both read and write to the partition.  You can make sure that you have that installed by running synaptic package manager and seeing if that is installed).

After you are done editing fstab, you need to create the directory that it's going to mount the partion on so you need to run the following in Terminal:

```
sudo mkdir /media/XP
sudo mount -a
df -h
```

I don't quite understand how the second line works and I don't know what the third line does, but I found that part at [this thread]("http://ubuntuforums.org/archive/index.php/t-1023491.html") ([http://ubuntuforums.org/archive/index.php/t-1023491.html](http://ubuntuforums.org/archive/index.php/t-1023491.html)).

So all of this together worked for me, and I hope it helps all of those who are as lost on this subject as I was.

---

### Post by edog76 on 2009-01-03
There's also this [tutorial](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by rubberbandiv on 2009-02-06
> I don't quite understand how the second line works and I don't know what the third line does,

```
sudo mount -a
```
The "mount" command mounts filesystems, and when you give it the -a switch, it mounts all the filesystems mentioned in /etc/fstab (makes sense, "a" for "all").

```
df -h
```
I'm not sure if this one is necessary in this process, because all it does is report how much space is left on the mounted partitions/disks.  "-h" means "human-readable" - normally df outputs bytes free, -h translates those to megabytes and gigabytes.

Something that is pretty important for all of this, though: BACK UP YOUR FSTAB before editing it.  Do
```
sudo cp /etc/fstab /etc/fstab.backup
```
which copies (cp) /etc/fstab to a new file called /etc/fstab.backup.  That way, if your new fstab is messed up, you can always go back to the backup and have a usable system again.

---

