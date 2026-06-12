---
title: "Few questions about defragging and ext3/ntfs"
date: 2009-02-16
forum: General Help
---

### Post by pickboy87 on 2009-02-16
Alright, so I've been on/off linux/ubuntu for several years and finally took the full plunge to Ubuntu. Having used Windows...for...well, close to probably 10-15 years, I know that the file system they use tends to get fragmented rather easy. I just had a couple questions about formating/sharing/defragging the hard drives I have now.

I have 3 drives hooked up right now. Main drive 250gb is ext3, my Downloads/backup drive is 250gbs and is formatted in NTFS. This drive gets the most moved/deleted files. I also have a 500gb drive for my music which is also NTFS.

1. Is there any program to defrag drives that are NTFS in linux?
2. Would converting a drive to ext3/4 need to be defragged first?
3. I have a network setup with Samba to a computer that is running Windows XP, if I converted the downloads drive to ext3/4 would the shared folders still be seen by Windows?
4. How would I go about formating a drive to an ext4 file system or if that's not viable, ext3?
5. Would my drive benefit more so from ext3/4 vs. NTFS?
6. Is there any way to change the file system without having to move everything, format it, and transfer everything back?
7. Will Ubuntu auto-mount ext3/4 file systems or will I still have to click the drive to mount it when I log-in each time?

I thought I had more questions or better wording of these questions in my head, but maybe not... Still learning linux, pretty well versed in Windows though, so things are still a little new...sorta, but not really :P

I assume I might have to use GParted to format the drive, but is there an easier way of doing it inside of linux like there is in Windows? Thanks for your time!

-Nathan

---

### Post by oldos2er on 2009-02-16
ext4 will not be available in Ubuntu until 9.04 is released (with the 2.6.28.x kernel). No need to 'defrag' if you're going to reformat. The answer to #5 depends on which OS you're going to use. Native file systems (NTFS for Win*, ext3 for Linux) are always the best, and often the only, solution--to my knowledge, Win* will not install to or run on ext3. 

 Formatting is a destructive process.

Ubuntu will automount any partition you want it to (you may need to edit your /etc/fstab).

---

### Post by mb_webguy on 2009-02-16
1) No
2) No (since it would be reformatted)
3) Yes, since Samba doesn't care about the foreign filesystem
4) Use GParted from the Ubuntu LiveCD.  I'm not sure that it supports ext4, but it does ext3.  The [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), on the other hand, supports more filesystem types, including ext4.  Using a LiveCD is best, since a drive cannot be mounted when you're modifying partitions.
5) It depends on what you consider a benefit.  If you're primarily using Linux, it's nice to have ext3 since ntfs doesn't use Linux-style permissions.  You don't really have to worry about filesystem maintenance (i.e. defragging) in ext3 like you do with ntfs.  On the other hand, if you're dual-booting, you might want a shared partition to be ntfs since Linux handles ntfs better than Windows handles ext3. And Windows won't run on a non-Windows filesystem (even if it can use such filesystems).
6) Nope
7) If you create the partition during the installation process, then the partition will be automatically adds an entry to the fstab file, and the partition will be automatically mounted on startup.  Otherwise, you'll need to manually add the fstab entry.

---

### Post by Phlee on 2009-02-16
Unix/Linux Ie EXT3 Filesystems Fragment?:)

Thought that was another reason why you switched to Ubuntu;)

---

### Post by pickboy87 on 2009-02-17
> **mb_webguy said:**
> 1) No **I figured, but that just gives me more reason to completely switch over to the ext3 file system.**
2) No (since it would be reformatted) **Yeah I figured...nevermind, I got it mixed up with partitioning...defrag before dual-booting, not single-booting. Nevermind :P**
3) Yes, since Samba doesn't care about the foreign filesystem
4) Use GParted from the Ubuntu LiveCD.  I'm not sure that it supports ext4, but it does ext3.  The [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), on the other hand, supports more filesystem types, including ext4.  Using a LiveCD is best, since a drive cannot be mounted when you're modifying partitions. **I'll be able to unmount the drive within linux. It's not a main drive that's running my OS, its just there for downloads.**
5) It depends on what you consider a benefit.  If you're primarily using Linux, it's nice to have ext3 since ntfs doesn't use Linux-style permissions.  You don't really have to worry about filesystem maintenance (i.e. defragging) in ext3 like you do with ntfs.  On the other hand, if you're dual-booting, you might want a shared partition to be ntfs since Linux handles ntfs better than Windows handles ext3. And Windows won't run on a non-Windows filesystem (even if it can use such filesystems). **Yeah, I know Windows won't run on ext3. I don't plan on dual-booting, and if I did have to for some reason use windows (*cough*games*cough*), then I would just use the other computer that's running XP. So I figure an all out system with ext3 would be better than half ext3 and half NTFS**
6) Nope **Also figured, I just remember hearing that ext3 can be upgraded to ext4 without destroying the whole partition...maybe I read it wrong. I kind of figured it didn't work that way for NTFS to ext3 though :)**
7) If you create the partition during the installation process, then the partition will be automatically adds an entry to the fstab file, and the partition will be automatically mounted on startup.  Otherwise, you'll need to manually add the fstab entry. **Alright, I'll dig around for information on adding drives to fstab. I wasn't sure if it wasn't mounting automatically because it was NTFS or if it just wasn't added to some boot file or something**


@ Phelee - Linux file system still gets fragmented...just not nearly as bad as windows. But yes, thats one reason :P


Oh, and I have one more question, if I do the file system to ext3, can I upgrade it to ext4 without a full reformat?

---

### Post by oldos2er on 2009-02-17
> **Phlee said:**
> Unix/Linux Ie EXT3 Filesystems Fragment?:)

Thought that was another reason why you switched to Ubuntu;)

 Every file systems fragments. ext3 fragmentation should only begin to cause slow down or other problems when it's 95% full.

---

