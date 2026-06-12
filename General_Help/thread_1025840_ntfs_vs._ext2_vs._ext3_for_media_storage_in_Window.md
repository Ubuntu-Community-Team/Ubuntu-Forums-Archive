---
title: "ntfs vs. ext2 vs. ext3 for media storage in Windows/Ubuntu?"
date: 2008-12-30
forum: General Help
---

### Post by sbfisher on 2008-12-30
What's my best file system choice for access from both Vista and Ubuntu?  I got a new external hard drive for storing many media files such as MP3s of my whole music collection, my digital camera raw files (~10MB each), many jpg files, etc.

I won't be running any programs from the file system, just for storing files and I have the Windows ext2ifs driver installed. I run Vista more than half of the time.   I'll be making monthly images of my entire system using Clonezilla (a Ghost-like open source bootable CD).

Is NTFS a better choice than ext2 because of journaling? Or is ext2 better at working with many files or nearly full volumes or uses drive space better? Any point in making it ext3 when the ext2ifs driver for Windows mounts as ext3 as ext2?  The volume will mostly be for reading and storing files (only small amount of writing) do the journaling features of ext3 or NTFS really a big benefit in this situation?

Any feedback would be very appreciated so I can figure out how to format my mostly media storage drive.

---

### Post by sdennie on 2008-12-30
I would probably go with NTFS in this case.  Simply because it's probably an easier solution because linux has native NTFS support whereas Windows doesn't have native ext2 support.  If you go with NTFS on external media, it's going to cause fewer headaches when you want to read that media somewhere else.  Even moving an ext2 disk between linux machines can cause annoyances because of permissions problems.

---

### Post by sbfisher on 2008-12-30
> **vor said:**
> I would probably go with NTFS . . . it's going to cause fewer headaches when you want to read that media somewhere else.  Even moving an ext2 disk between linux machines can cause annoyances because of permissions problems.

I hadn't even considered ext2 permissions problems on different Linux machines.  Sounds like NTFS is the most practical for my situation with media storage across platforms and machines.  Thanks.

---

### Post by thraxy on 2008-12-30
I'm using FAT32 on my external. I switched from NTFS because of mounting difficulties. At one point I had to force mount the NTFS drive every time I wanted to use it. I think that bug has been fixed since then, but FAT32 works just fine for me, so I'm sticking with that.

Pros: Works on all platforms.

Cons: 4GB max filesize (unhandy if you store large ISO files)

---

### Post by scrime on 2009-01-06
I am in the exact same situation, dual booting XP and Ubuntu, I think that Ext2ifs was causing my Ubuntu bootup to mess up, it kept bombing out on boot saying that checkfs (i think it's called that) was reporting errors.  Anyway I set ext2ifs to only do read-only mode and seems to have been working fine except when I share folders through XP on the EXT3 drive the files people copy are mostly corrupted.  I however can read them fine.

I'm going to do a total reformat now I'll dual boot both OS's on the first drive and set my main big drive (500gb) to NTFS, makes sense cause I think FAT32 has limitations on partition size and EXT3 is not working out for me.

---

### Post by scrime on 2009-01-06
I've never had a problem accessing NTFS from Linux, only if the NTFS drive hasn't been safely removed then I have to mount with -o force option to reset the log.  Otherwise never had a problem and been using it for years.

---

