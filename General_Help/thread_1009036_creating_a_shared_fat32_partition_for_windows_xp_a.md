---
title: "creating a shared fat32 partition for windows xp and ubuntu 8.1?"
date: 2008-12-12
forum: General Help
---

### Post by jar23d on 2008-12-12
I have about 15gigs of music and another 5gigs of video and i would like to create a way i could use this media in both windows and linux because i just dont have the disk space to keep it in both partitions. Whats the safest/easiest way to go about doing this?

---

### Post by pseudonym on 2008-12-12
If you want a shared partition it doesn't need to be fat32 anymore. Since Gutsy (I think) Ubuntu has worry-free ntfs read/write by default using ntfs-3g.

If your files are already stored on an ext3 partition you can read/write them from Windows using an IFS ('installable file system') driver. I've used [FS-Driver]("http://www.fs-driver.org/") for 2 years without any problems. To be on the safe side, however, I'd make sure your ext2/3 partition is *not* your Linux root partition.

HTH

---

### Post by Andreas1 on 2008-12-12
> **jar23d said:**
> I have about 15gigs of music and another 5gigs of video and i would like to create a way i could use this media in both windows and linux because i just dont have the disk space to keep it in both partitions. Whats the safest/easiest way to go about doing this?

i would use **gparted**, the gnome partition editor, to shrink the other two partitions and create a new one.
i think it is no longer included in the default installation, so you have to install it via synaptic.
and as pseudonym said, you can make it ntfs as well as fat32, since linux can do both. the main advantage of ntfs would be that you can store files that are bigger than 4gb.

---

