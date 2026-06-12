---
title: "Drag-and-Drop"
date: 2006-06-13
forum: Desktop Environments
---

### Post by dstein on 2006-06-13
I wanted to transfer some of my files on my Winodows desktop to my linux desktop, so from the terminal, I typed "gksudo nautilus". Then in Nautilus, I found my Windows Desktop Folder in /tmp/disks-conf-hda1/Documents and Settings/Daniel/Desktop. When I try transferring the files by draggin-and-dropping, nothing happens. Is there a better way to do this? Thanks.

---

### Post by Ubuntuud on 2006-06-13
Have you already tried the old-fashioned way? (copy, paste)

---

### Post by dstein on 2006-06-13
Yeah, I also gave that a shot. Is there something wrong with the way the drive is mounted maybe. It's on another drive. I think I'll try to do it all from the terminal. Any suggestions would be great. Thanks.

---

### Post by bruce89 on 2006-06-13
tmp/disks-conf-hda1/Documents and Settings/Daniel/Desktop doesn't sound right.

Open System &#8594; Administration &#8594; Disks
Select the correct hard disk, and click the Partitions tab.
Select the relevant partition, and click Enable.
To unmount the partition, click Disable.

---

### Post by dstein on 2006-06-13
It is already mounted, and it says that the access path is "/tmp/disks-conf-hda1". When I click Browse, it brings me to an empty folder, and when I move up a directory, the icon is a folder that has a big x to the top right and a lock to the bottom right. Any advice??

---

### Post by ayoli on 2006-06-13
weird path to mount a disk, usually every dev automatically mounted are located in /mnt or /media
if it is really mounted whereyou said, do you have right perms to browse this folder ?

---

### Post by CatKiller on 2006-06-13
[QUOTE=dstein]I wanted to transfer some of my files on my Winodows desktop to my linux desktop, so from the terminal, I typed "gksudo nautilus". Then in Nautilus, I found my Windows Desktop Folder in /tmp/disks-conf-hda1/Documents and Settings/Daniel/Desktop. When I try transferring the files by draggin-and-dropping, nothing happens. Is there a better way to do this? Thanks.[/QUOTE]

The Disk Manager does seem to put the mount point in /tmp/ unless you've explicitly mounted them somewhere else, and unfortunately they're owned by root (argh!) so you, as a regular user, can't read it. And when I've tried to chown with sudo in the past, it hasn't worked because it can't/won't write permissions on the NTFS filesystem that that partition was using.

The way I would do it is to ignore the Disk Manager completely and have a look in the Ubuntu Guide for "How to mount/unmount Windows partitions manually" and do it that way. Don't forget to create your mount point first.

---

