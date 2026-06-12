---
title: "Ready to migrate. Need help using dd."
date: 2009-03-22
forum: General Help
---

### Post by umanzor on 2009-03-22
Hi everyone, I've been trying Ubuntu for quite sometime now (since 2005 I belive), constantly moving from Linux to Windows back and forth every few months. I've testing the Windows 7 beta since December (yup, I'm one of those) and been using Vista before that. Recently I moved back to Ubuntu because a coworker was trying it out and I gave him some tips on it. This made me want to come back, and after a month or so, I think I'm ready to completely migrate. 

Basically, I want to move my Ubuntu install to another hard drive. So, I currently have 3 hard drives.

*sda: ~200GB
**sda1: 200MB partition made by the Windows 7 installer.
**sda2: 189GB partition dedicated completely to windows, and my documents.

*sdb: ~40GB
**sdb1: 34GB partition in ext3 that has my Ubuntu installation.
**sdb2: 1.68GB swap partition
**~1GB unallocated.

*sdc: ~500GB
**sdc1: 455GB NTFS partition that has all my media files (music, movies, tv, etc)
**sdc2: 9.77GB FAT32 partition I was using to watch videos on my PS3. (long story short, uPnP servers were not working with 7, so I had to use this to watch my media, now I'm using Mediatomb so I don't need it, but this is pretty much irrelevant :) )

What I want is this. Move my Ubuntu partition (and swap partition) to sda. sdb will have two partitions, one for my home directory and the other one will be a Windows partition. sdc is just sdc.

So, two things, I'm thinking of using dd to copy and move the ubuntu partition. Then, I don't know if it is possible to move the location of the home directory. But if it is then I'll do that.

So since it looks like a very long thing, I'm wondering if it would be better to just reinstall altogether.

tl;dr What can I use to move my Ubuntu partition to another hard drive? Is it possible to move the home directory?

---

### Post by dcstar on 2009-03-23
> **umanzor said:**
> Hi everyone, I've been trying Ubuntu for quite sometime now (since 2005 I belive), constantly moving from Linux to Windows back and forth every few months. I've testing the Windows 7 beta since December (yup, I'm one of those) and been using Vista before that. Recently I moved back to Ubuntu because a coworker was trying it out and I gave him some tips on it. This made me want to come back, and after a month or so, I think I'm ready to completely migrate. 

Basically, I want to move my Ubuntu install to another hard drive. So, I currently have 3 hard drives.

*sda: ~200GB
**sda1: 200MB partition made by the Windows 7 installer.
**sda2: 189GB partition dedicated completely to windows, and my documents.

*sdb: ~40GB
**sdb1: 34GB partition in ext3 that has my Ubuntu installation.
**sdb2: 1.68GB swap partition
**~1GB unallocated.

*sdc: ~500GB
**sdc1: 455GB NTFS partition that has all my media files (music, movies, tv, etc)
**sdc2: 9.77GB FAT32 partition I was using to watch videos on my PS3. (long story short, uPnP servers were not working with 7, so I had to use this to watch my media, now I'm using Mediatomb so I don't need it, but this is pretty much irrelevant :) )

What I want is this. Move my Ubuntu partition (and swap partition) to sda. sdb will have two partitions, one for my home directory and the other one will be a Windows partition. sdc is just sdc.

So, two things, I'm thinking of using dd to copy and move the ubuntu partition. Then, I don't know if it is possible to move the location of the home directory. But if it is then I'll do that.

So since it looks like a very long thing, I'm wondering if it would be better to just reinstall altogether.

tl;dr What can I use to move my Ubuntu partition to another hard drive? Is it possible to move the home directory?

Simply boot off an Ubuntu Live CD and use the Partition Editor to copy and paste partitions.

Be aware that the UUIDs remain the same, so you need to disconnect the old drive (or delete the partitions) to avoid a clash.

You should set up a separate /home partition, you can search out instructions for this.

---

