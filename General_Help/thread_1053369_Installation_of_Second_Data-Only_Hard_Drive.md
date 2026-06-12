---
title: "Installation of Second Data-Only Hard Drive?"
date: 2009-01-28
forum: General Help
---

### Post by siabost on 2009-01-28
Hi,

I have a Dell Dimension 2400 Desktop with Celeron 2.4Ghz processor dual-booting Win XP & (more importantly) Ubuntu 8.04.

The current hard drive is a 40GB IDE unit & I'm considering adding a second 160GB hard drive purely for data (music mostly) - a kind of /home#2 for Ubuntu.
I would still be booting from the original drive.

How do I go about configuring the drive as /home#2 & how does this affect the existing swap partition?

Many thanks for any help.:D

---

### Post by Gizenshya on 2009-01-28
Will the drive be internal, or in an external enclosure?

whatever the case, all you need to do is format the drive (it will probably come with a disk to do it at boot), or you can format from win or ubuntu.  NTFS would likely be your best bet, for win compatibility (and you can have files over 4 gb).

once formatted.. thats it. just mount it (though it will likely be automounted anyway) and copy and paste :)

and if it will be internal, you can edit your fstab and have it mounted at startup to wherever you like.

---

### Post by siabost on 2009-01-29
Hi,

Thanks.

The hard drive would be internal.

As I would be using Ubuntu to access the data on this drive I was thinking of formatting it in ext3 but... Can NTFS be read/written to as efficiently by Ubuntu as well as WinXP? Advantages & disadvantages?

Will Ubuntu see this new drive as a partition or as a separate drive?

Editing fstab - I run Gnome. I take it this will be located in the boot folder and edited via something like: sudo gedit /(location of)/fstab ?
Hopefully it'll be obvious what I should edit (as I've not done this before) but trial & error should sort that out!

Many Qs I know, but thanks again. :D

---

### Post by -kg- on 2009-01-29
> **siabost said:**
> Hi,

Thanks.

The hard drive would be internal.

As I would be using Ubuntu to access the data on this drive I was thinking of formatting it in ext3 but... Can NTFS be read/written to as efficiently by Ubuntu as well as WinXP? Advantages & disadvantages?

Will Ubuntu see this new drive as a partition or as a separate drive?

Editing fstab - I run Gnome. I take it this will be located in the boot folder and edited via something like: sudo gedit /(location of)/fstab ?
Hopefully it'll be obvious what I should edit (as I've not done this before) but trial & error should sort that out!

Many Qs I know, but thanks again. :D

First question: yes, Ubuntu can read and write to ntfs quite well.

Second question: It will see it as both.  Your primary drive will be recognized as hda or sda, and the partitions contained on it will be a number, i.e., hda1 or sda2.  The second hard drive will be hdb or sdb, with any partitions on it again being represented by a number.

Third question: The location will be /etc/fstab, as in:

```
gksu gedit /etc/fstab
``` 

Fstab is a teeny bit complicated, depending on what you want to do with it.  A very good tutorial follows:

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by siabost on 2009-02-02
Hi,

Well, green though I am, I finally managed to get my second drive initialized & formatted.
As I'm dual-booting WinXP + Ubuntu8.04 I used XP to format it in NTFS (didn't know how in Ubuntu).
I added the last two lines to fstab & the drive mounts on boot.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0ab16d95-24a0-4436-ab28-124361f7a3ec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=4b41da5e-1b92-4781-a534-93f2d50b0236 /home           ext3    relatime        0       2
# /dev/sda1
UUID=7E7411C774118357 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=98162e38-6e78-492c-91bd-b78e2e3a7a4c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,auto,exec,utf8 0       0
# /dev/sdb1 (Music Hard Drive)
UUID=30F838A9F8386F6A /media/Music        ntfs-3g    rw,users 0       3
So far so good, but any folder I create on this drive is owned by "root" & I haven't been able to change this which makes it unpredictable (for instance) when writing metadata to music files.

EDIT: Tried adding umask, uid & gid settings into the "Options" part of the last line above (as per the tutorial in -kg-'s post)but without any change.
Can I get round all this by formatting the drive in Ubuntu rather than XP? If so how do I do it?

Thanks so far & I look forward any pointers.:p

---

### Post by siabost on 2009-02-03
Is it possible I don't "own" the hard drive? Permissions to an NTFS formatted drive are loaded at boot, I believe, via fstab?

Thanks

---

### Post by -kg- on 2009-02-04
I was having a bit of similar trouble with my Music ntfs partition, and through a little experimentation I found what worked.

In my fstab, I have referred to all my ntfs partitions as "dev/sd<letter>(#)" (i.e., not by the UUID).  Options are set to "default".

First, change "ntfs-3g" to plain "ntfs".  Reboot, and of course the partition will be auto-mounted.  Only root will be able to unmount.  Edit your fstab again and comment that line out, then reboot.

When I did this, I was able to mount the volume through Nautilus, after which I was able to mount and unmount it at will.  If you want the volume to auto-mount, just leave the line uncommented.

I have found that I can write to the volume as well as read it without ntfs-3g.  Something in the regular "driver" must have been updated.  Try it and see if it works for you.

---

### Post by siabost on 2009-02-04
Thanks -kg-

I will try that... once I can get back into Ubuntu!

In my impatience I loaded GParted & formatted the drive in ext3 (my version doesn't do NTFS yet) from my primary hard drive.
This seemed to work ok though it only took 5mins (?)
I then edited fstab and added the a new line for it by copying that for my /home partition & changing the UUID, mount point & pass to suit.
I now can't boot into Ubuntu - I get the grub list but nothing loads. Have tried "recovery" and got as far as a shell. I can edit my fstab from there but I can't figure how to save my changes.
How do I save changes in the recovery shell?

Off course, I'm assuming that fstab is the problem.

I'm considering loading Ubuntu 8.10 if sorting my 8.04 proves too nerve-fraying;)!
But I'll have another stab at fstab in my current set-up if someone can advise me on the "saving" issue.

Many thanks.

---

### Post by -kg- on 2009-02-07
Sorry I was away for so long.  Things have been hectic the past few days.

What were you using to edit fstab from the command line?  Whatever it is that you're using, you need to look at the documentation and find out how to save changes once you've made them.

For example, if you're using vim, the following is from the vim help files:

> To exit, use the "ZZ" command.  This command writes the file and exits.

	Note:
	Unlike many other editors, Vim does not automatically make a backup file.  If you type "ZZ", your changes are committed and there's no turning back.  You can configure the Vim editor to produce backup files, see |07.4|.


Of course, if you want a backup file, you will need to execute:

```
cp /etc/fstab /etc/fstab-backup
```

There are a number of command line editors available, and of course they will vary as to how the file is saved.  Usually, they will have a set of help files available, or you can find tutorials on the web with a search engine search.

However, I doubt seriously that problems with fstab caused your booting problem.  The fstab configuration file is primarily to enable automatic mounthing of partitions at boot time.  It's more likely a GRUB menu.lst problem, though I can't figure why editing fstab would affect the menu.lst.

It may possibly be the erroneous entry in the fstab that points to the former ntfs partition is the problem, as that partition no longer exists as such.  If that line is there it might help to delete it from fstab, then recreate it properly once you get back into Ubuntu with the correct UUID or whatever method you use to refer to it.

Oh!!! A moment.  I just re-read your last post:

> I then edited fstab and added the a new line for it by copying that for my /home partition & changing the UUID, mount point & pass to suit.

When you changed it to be the new mount point for /home, you did copy all the necessary files and folders over to the new /home partition, right?  As I remember, /home contains some configuration files that Ubuntu needs to operate correctly for the individual users.  That is the main reason to create a separate /home partition...to save user settings and configurations during an Ubuntu (or other Linux distro) upgrade.  If those files are not present, you won't be able to load those settings at boot time, thus, only a command line interface in Recovery mode.

I don't know...I'm a little out of my league here.  Hopefully someone can come up with a solution.  I am just guessing and surmising here.

---

