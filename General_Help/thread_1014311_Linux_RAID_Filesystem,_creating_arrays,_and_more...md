---
title: "Linux RAID Filesystem, creating arrays, and more..."
date: 2008-12-17
forum: General Help
---

### Post by cforceleritas on 2008-12-17
Hello All

I have a bit of a problem on my hands, spurred by lack of experience using Linux RAID and possibly linux in general.  Any suggestions/help I can get here would be VERY much appreciated.

To summarize, I had a RAID-1 (mirror) array set up between 2 drives.  I acquired a third drive of the same size, so I thought I would transform my RAID-1 into a RAID-5 array.  Of course I wanted to do this while preserving the data on the 2 drives that used to be mirrored.

Well, I started by:
```
sudo mdadm --stop /dev/md0
sudo umount /dev/sda
sudo umount /dev/sdd
sudo umount /dev/sde
```

sda/d/e are the 3 drives I'm wanting to convert to RAID-5.

Next, I used mdadm to create a RAID-5 array, and by every indication I could see this step succeeded.

The problem came when I tried to mount the newly created (RAID-5) /dev/md0.  I received a message from mount saying bad filesystem or something similar...

After reading back over the guide I was using I saw that I had to mkfs.ext3 /dev/md0 to get the array into an ext3 filesystem to be mounted.

I fear this is where I lost my data, though I thought that mkfs.ext3 would preserve data.

So, after using mkfs.ext3 (I bet you know what I'm about to say) the array mounted correctly but there was no data on it, and dolphin said I had the full size of it available.

What I want to know is how, if possible, to recover this data.  I have tried mounting a single drive that used to be mirrored, but mount doesn't understand the linux-autodetect filesystem (from fdisk -l).  I have tried reverting to the mirror with the same 2 drives, and there is no data.

Is it possible to mount linux-autodetect filesystem somehow?

Is it possible to create a single disk array with mdadm so that I can get to the data?

I think that all the data should be there, but I have exhausted everything I can think of to get to it.

I know that there are going to be replies that I should have backed up everything, and I can't argue there.  This is not critical data, but I have spent several years collecting and organizing it, so I am trying everything I can do to repair it.

I appreciate any help someone may provide.

---

