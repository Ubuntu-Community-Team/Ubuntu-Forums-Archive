---
title: "Can't play VCD/DVD, etc."
date: 2006-01-08
forum: General Help
---

### Post by endangst on 2006-01-08
I can't play VCDs in Xine or Totem.  Totem will tell me "Failed to find mountpoint for device /dev/hdc in etc/fstab".

I read about the automount problem and my fstab file is normal like everyone else's...from what I could gather, this is a bug. :( 

Xine won't play VCDs either.

I then decided to download VLC and it will play VCDs, but I get static or crackle in the audio every now and then...just doesn't sound right.

What should I do?  Should I download Mplayer?  

Two things are keeping me from abandoning Windows now:
 
1.  C-media card reader is detected but won't read xD card in Linux.
2.  Problems playing VCDs and DVDs in the media players that come with Ubuntu

I greatly appreciate any help.  I don't know much about Linux.  I'm just a newbie, but I've kept reading the forums and Googling, but can't seem to fix these problems.

Thanks!

---

### Post by judgekaster on 2006-01-08
a) do make sure that you have an entry (a line) in your /etc/fstab file pointing where /dev/hdc (assumably your cdrom device) should be mounted. typically, there would be a line like:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and

b) make sure that the mount point (the second column entry, in this case "/media/cdrom0") actually exists. if it does not exist, create it with

sudo mkdir /media/cdrom0

---

### Post by endangst on 2006-01-08
Here is what my etc/fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/xpsys	ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/xpdata	ntfs    nls=utf8,umask=0222 0       0

Here's what happened when I tried to mkdir:
 
endangst@ubuntu:~/Desktop$ sudo mkdir /media/cdrom0
Password:
mkdir: cannot create directory `/media/cdrom0': File exists
 
Is there a way for me to open that file?  I can't seem to open /media/cdrom0 with gedit.

---

### Post by Jammy_Stuff on 2006-01-08
It's a directory and when you open it, it will show you the contents of the CD in your drive.

---

### Post by judgekaster on 2006-01-08
/media/cdrom0 is a directory and it is there where your cdrom is supposed to be mounted.

try inserting a cdrom, then issue the following command in your terminal:

sudo mount /media/cdrom0

---

