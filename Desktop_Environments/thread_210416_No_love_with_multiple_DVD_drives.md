---
title: "No love with multiple DVD drives"
date: 2006-07-06
forum: Desktop Environments
---

### Post by ddales on 2006-07-06
I just switched from Opensuse to Ubuntu a couple of weeks ago and need some help!?  I really like Ubuntu but it's pissing me off now.

Ubuntu doesn't see my DVD Recorder.

I have hunted through all the forums and googled my *** off but can't seem to figure this out.

My FSTAB:
proc            /proc           proc    defaults        0       0
/dev/sda3       /               reiserfs defaults        0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sdb1       /home           reiserfs defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

My DEV/CD?
lrwxrwxrwx 1 root root 3 2006-07-06 23:22 cdrom -> hdb
lrwxrwxrwx 1 root root 3 2006-07-06 23:22 cdrw -> hdb

My DEV/DVD?
lrwxrwxrwx 1 root root 3 2006-07-06 23:22 dvd -> hdb
lrwxrwxrwx 1 root root 3 2006-07-06 23:22 dvdrw -> hdb

My MEDIA/
lrwxrwxrwx 1 root root  6 2006-07-04 16:36 cdrom -> cdrom0
drwxr-xr-x 2 root root 48 2006-07-04 16:36 cdrom0

As we can see, my fstab is lacking my /dev/hdb devices for my dvd-rw

With Suse I know how to fix this, you make the dirs in /media and edit the fstab to reflect the changes.  However, Ubuntu doesn't seem to understand this.

Please help and thank you in advance!

---

### Post by simonn on 2006-07-06
Is there a drive on hda on your system?

---

### Post by Dubbayoo on 2006-07-06
I have both a DVD-ROM and a DVD-Burner. Only one appears in fstab but my Dapper system will automount a disk in either one. The reader is scsi and the burner is ide.


My FSTAB

steve@ubu:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /data           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# added by me
jeeves:/home    /mnt/home       nfs     rw,hard,rsize=8192,wsize=8192,timeo=14,intr     0       0
jeeves:media    /mnt/music      nfs     rw,hard,rsize=8192,wsize=8192,timeo=14,intr     0       0


My DEV/CD

steve@ubu:/media$ ll /dev/cd*
lrwxrwxrwx 1 root root 4 2006-07-06 18:41 /dev/cdrom -> scd0
lrwxrwxrwx 1 root root 3 2006-07-06 18:41 /dev/cdrw -> hdc

My DEV/DVD
steve@ubu:/media$ ll /dev/dvd*
lrwxrwxrwx 1 root root 4 2006-07-06 18:41 /dev/dvd -> scd0
lrwxrwxrwx 1 root root 3 2006-07-06 18:41 /dev/dvdrw -> hdc


My MEDIA

steve@ubu:/media$ ll /media/
total 12K
lrwxrwxrwx  1 root  root     6 2006-07-04 16:51 cdrom -> cdrom0/
drwxr-xr-x  2 root  root  4.0K 2006-07-04 16:51 cdrom0/
dr-xr-xr-x 13 steve steve 4.0K 2006-05-30 20:16 cdrom-1/
drwxr-xr-x  2 root  root  4.0K 2006-07-06 06:22 ipod/

---

### Post by simonn on 2006-07-06
> **Dubbayoo said:**
> my Dapper system will automount a disk in either one. 


So what is the actual problem?

---

### Post by Dubbayoo on 2006-07-07
> **simonn said:**
> So what is the actual problem?

He can't use his dvd burner. 

What happens if you insert a blank disk in the burner? I get a prompt to format the disk.

---

### Post by ddales on 2006-07-12
Ok, I was out of town for a few days but now back at trying to solve this problem.

I did some more hunting around and made the following changes where I added directories and links for the DVD devices:

FSTAB
lrwxrwxrwx 1 root root  6 2006-07-04 16:36 cdrom -> cdrom0
drwxr-xr-x 2 root root 48 2006-07-04 16:36 cdrom0
drwxr-xr-x 2 root root 48 2006-07-12 07:18 cdrom1
lrwxrwxrwx 1 root root  6 2006-07-12 07:21 cdrw -> cdrom1
lrwxrwxrwx 1 root root  4 2006-07-12 07:41 dvd -> dvd0
drwxr-xr-x 2 root root 48 2006-07-12 07:29 dvd0
drwxr-xr-x 2 root root 48 2006-07-12 07:29 dvd1
lrwxrwxrwx 1 root root  4 2006-07-12 07:41 dvdrw -> dvd1

MEDIA DIR  (added the DVD directories and links)
lrwxrwxrwx 1 root root  6 2006-07-04 16:36 cdrom -> cdrom0
drwxr-xr-x 2 root root 48 2006-07-04 16:36 cdrom0
drwxr-xr-x 2 root root 48 2006-07-12 07:18 cdrom1
lrwxrwxrwx 1 root root  6 2006-07-12 07:21 cdrw -> cdrom1
lrwxrwxrwx 1 root root  4 2006-07-12 07:41 dvd -> dvd0
drwxr-xr-x 2 root root 48 2006-07-12 07:29 dvd0
drwxr-xr-x 2 root root 48 2006-07-12 07:29 dvd1
lrwxrwxrwx 1 root root  4 2006-07-12 07:41 dvdrw -> dvd1

DEV DIR
lrwxrwxrwx 1 root root 3 2006-07-12 07:48 cdrom -> hda
lrwxrwxrwx 1 root root 3 2006-07-12 07:48 cdrw -> hdb
lrwxrwxrwx 1 root root 3 2006-07-12 07:48 dvd -> hda
lrwxrwxrwx 1 root root 3 2006-07-12 07:48 dvdrw -> hdb

When I insert a blank DVD I see the icon appear on the desktop for about 2 seconds and get prompted to:  Ignore or Create DVD  :then both disappear by themselves.

When trying to use GnomeBaker, the burn fails but doesn't tell me why.  When trying to use K3B, it says that the data will not fit on the disc.
When trying to play a DVD, it works fine with Xine, Totem or Mplayer.

It's as if the system refuses to recognize the DVD drives as DVDs and will only use/mount them as CD devices.

](*,)

---

### Post by ddales on 2006-07-12
Well, this is kindof fixed.  I got all my drives working with whatever app I choose to use.

Still have one strange thing which is a 4.4 ISO Image gets reported as being too big for the media.  I think this is simply a matter of playing with the app that I use to build the ISO.

Thanks for your help!

---

