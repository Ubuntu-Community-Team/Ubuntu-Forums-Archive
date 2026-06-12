---
title: "[SOLVED] Mounting HDD's in Live CD"
date: 2006-06-23
forum: Desktop Environments
---

### Post by stalker145 on 2006-06-23
I have been using Dapper since it came out for my laptop and have thought of giving it a run for my server, but I've come upon a big hinderance. Many of you have mentioned running with the Live CD for a while and I am taking that advice. I wonder if this, though, is what's causing my problem.
My server has six separate HDD's, only one of which mounts upon booting the Live CD. I found a nice walk-through at Psychocats ([http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)) that doesn't really help since my fstab file looks absolutely nothing like what they show.
Mine looks like this :

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

That's it... nothing more, nothing less. The basic question is: is this a problem with running the Live CD and expecting too much or am I missing some easy item? If it's the Live CD, are the directions at Psychocats correct for what I'm looking to do once I take the step and install?
Thank you to everyone out there in this community. I haven't posted until now, but you've been a great help in getting me started on a new way of thinking. Hopefully I can start to contribute in the near future.

---

### Post by aysiu on 2006-06-23
For live CD sessions, you don't want to add the item to your /etc/fstab because that'll go away the next time you reboot.

Create a mount point for it: ```
sudo mkdir /tmp/harddrive
``` Then mount it manually: ```
sudo mount -t ntfs /dev/hda1 /tmp/harddrive -o nls=utf8,umask=0222
``` for NTFS or ```
sudo mount -t vfat /dev/hda1 /tmp/harddrive -o iocharset=utf8,umask=000
``` for FAT32. This assumes, of course, that your partition is /dev/hda1, but ```
sudo fdisk -l
``` will tell you what it really is.

---

### Post by stalker145 on 2006-06-23
aysiu, thank you for the quick response. It worked like a dream once I figured out that I was reading the fdisk wrong ;) And thank you for, as they say on my job, "breaking it down Barney-style" for me.
I don't know what most of the command meant that you showed me, but that will come with using Linux, I'm sure.

---

### Post by aysiu on 2006-06-23
I'll break it down for you:

**sudo**: with administrative privileges
**mount**: make it appear
**-t**: of filesystem type
**ntfs**: NTFS
**/dev/hda1**: the partition to make appear
**/tmp/harddrive**: the folder you want it to appear in
**-o**: with these options
**nls=utf8**: with UTF-8 character encoding
**umask=0222**: read-only for everyone

---

### Post by stalker145 on 2006-06-23
I think I understand the big one there. The umask is similar to chmod (which I've seen talked about and used, but not personally used). Had to do a bit of reading to figure it out with 022 equalling 755. Time to do more reading so that I can remember all of this.
Now, with the FAT32 umask being 000, is this due to Linux being able to natively read and write to that particular file system without difficulty? Dunno, just thinking here.

---

### Post by aysiu on 2006-06-23
Yes.
FAT32 read/write
NTFS read-only

---

