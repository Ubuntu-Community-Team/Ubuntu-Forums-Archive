---
title: "Need memory to burn DVDs from Live boot"
date: 2006-03-04
forum: Desktop Environments
---

### Post by soupface on 2006-03-04
My root partition is giving me some [scary "unable to read inode" messages]("http://ubuntuforums.org/showthread.php?t=62666&highlight=unable+read+inode"). I've resigned myself to a format-and-install, but would like to back up my documents and music before doing so.

I've booted using the Live CD and am able to mount and read my /home and /music partitions (FAT32). When I try to burn them to DVD, using GNOME's built-in burning tool, I get an error message telling me that there's not enough room to burn the files to the disc.

This of course, is not true: the blank DVDs and CDs have plenty of room. The problem is that there's not enough room in the temporary /home/ubuntu filespace to make a disc image.

Is there any way I can allocate extra space so that I can burn my documents onto DVD?

Thanks (in advance).

---

### Post by akiro.yamamoto on 2006-03-04
Do you have a fat32 or ext partition that you can mount as /tmp?
If so you can mount it as /tmp by setting up the fstab like:
/dev/hda2 /tmp user,auto 0 0
or something like that.

---

### Post by soupface on 2006-03-04
[QUOTE=akiro.yamamoto]Do you have a fat32 or ext partition that you can mount as /tmp?
If so you can mount it as /tmp by setting up the fstab like:
/dev/hda2 /tmp user,auto 0 0
or something like that.[/QUOTE]

I have an iffy FAT partition (/dev/hda6) that I could mount. I'm just not certain how I would add or remove it as temporary space: sudo mount /dev/sda8 /tmp doesn't cut it.

It seems that the burning tool fails because it's trying to create an image in the /home/ubuntu directory, not /tmp.

---

### Post by akiro.yamamoto on 2006-03-04
Can you boot into windoze?
If so your fastest bet is to use it to backup all your info before your format that drive.
You can try mounting the fat partition as /home or directing the CD software to
the fat part. mounted as /tmp.
Or you can use a live cd like SLAX or Puppy Linux , which are smaller live cds than 
the Ubuntu live CD.

---

### Post by soupface on 2006-03-04
No, I don't have Windows: I can boot into Ubuntu Live, off a CD.

The thing is that the space allocated to /home by default on a Live CD is always going to be too small to hold a whole DVD image. I want to know how to expand it.

---

