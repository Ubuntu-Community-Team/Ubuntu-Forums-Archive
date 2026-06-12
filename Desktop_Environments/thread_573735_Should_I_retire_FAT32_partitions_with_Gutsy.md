---
title: "Should I retire FAT32 partitions with Gutsy"
date: 2007-10-11
forum: Desktop Environments
---

### Post by plutino on 2007-10-11
Since Gutsy now has full support for NTFS system, should I still keep a FAT32 partition?  How stable is the current NTFS driver?

---

### Post by borris.morris on 2007-10-11
the driver in gutsy and feisty are full read write and are pretty stable. ive never had a probelm with it. i would fully reccomend switching because ntfs is better. it doesnt get fragmented as much, bigger file sizes capablilites, etc.

---

### Post by kostkon on 2007-10-12
I think yes, the driver it's pretty stable, you could switch to *NTFS*.

Now that *NTFS* is well supported in Linux, I believe the *FAT* file system will die quickly, it was about time (except for USB flash drives, of course).

---

### Post by peitschie on 2007-10-12
The only thing that I have had troubles with is Steam on NTFS.  If you want to share steam between linux & windows, best you keep the fat32.  Apart from that, I have been running without the ol' fat for a year now and haven't lost any files or partitions due to corruption :).  

Just make sure you keep windows installed though, as linux can occasionally get its fingers slammed in the door on a hard (non-safe) reboot.  This causes the ntfs partition to report its "dirty" (ew... touched by microsoft!), and refuse to mount it rw until windows has chkdsk'ed it.  Having said that, using the REISUB shutdown combination (hod alt+sys and type those letters slowly on a hard-lock to safely unmount everything) does seem to help prevent this.

---

### Post by ryanVickers on 2007-10-12
No need for FAT 32 anymore - less corruptible, larges single file capacities, etc.

---

### Post by MystaMax on 2007-10-12
> **kostkon said:**
> I think yes, the driver it's pretty stable, you could switch to *NTFS*.

Now that *NTFS* is well supported in Linux, I believe the *FAT* file system will die quickly, it was about time (except for USB flash drives, of course).

Hello, 

What do you mean by, "except for USB flash drives"?  I have an external 500gb (1 FAT32 & 1 EXT3) and a 4 gig thumb drive (1 FAT32). Can I go to NTFS?

Anyone use the [EXT2 driver]("http://www.fs-driver.org/") (which also [works with EXT3]("http://www.fs-driver.org/faq.html#acc_ext3") for windows)? Only reason why I haven't is because I move data between multiple computers, and would have to load the driver on each one I visit.

---

### Post by benerivo on 2007-10-12
I think he means thumb drives and mp3 players, both of which are still usually formatted with fat.

I did use the ext2 driver for windows, but for windows <> linux interoperability, i would use ntfs (using the ntfs-3g driver in linux).

---

### Post by ryanVickers on 2007-10-12
> **MystaMax said:**
> Hello, 

What do you mean by, "except for USB flash drives"?  I have an external 500gb (1 FAT32 & 1 EXT3) and a 4 gig thumb drive (1 FAT32). Can I go to NTFS?

Anyone use the [EXT2 driver]("http://www.fs-driver.org/") (which also [works with EXT3]("http://www.fs-driver.org/faq.html#acc_ext3") for windows)? Only reason why I haven't is because I move data between multiple computers, and would have to load the driver on each one I visit.

If you've got a drive that big (and probably important), then it's a good idea to make it ext3 if it's all Linux.  For flash drives (at least for now as they are only up to 4GB), FAT32 is still a good idea - I've got a 128MB one that's FAT16 ;)

---

### Post by skipbarker on 2007-10-12
I would make th switch.

---

### Post by inportb on 2007-10-12
> **MystaMax said:**
> Hello, 

What do you mean by, "except for USB flash drives"?  I have an external 500gb (1 FAT32 & 1 EXT3) and a 4 gig thumb drive (1 FAT32). Can I go to NTFS?

Anyone use the [EXT2 driver]("http://www.fs-driver.org/") (which also [works with EXT3]("http://www.fs-driver.org/faq.html#acc_ext3") for windows)? Only reason why I haven't is because I move data between multiple computers, and would have to load the driver on each one I visit.
Uh, if you have a 500GB USB drive, it's probably not a flash drive... anyway, i'd used ntfs-3g long enough to know that it's pretty stable, but now I use ext3fs all the way.

---

### Post by Orbital75 on 2007-10-12
I don't think they make a flash drive larger than 4 Gig at this time.
You have a USB hard drive.....

---

### Post by ryanVickers on 2007-10-13
Yes, that's the point - flash drives are good with FAT32, but anything else, ex. a HD regardless of how it's attached, should have a 'real' filesystem ;)

---

### Post by Xenaco on 2007-10-13
If you wish to depart with $150 you can get Flash (Thumb) drives up to 16GB now.

---

### Post by paxmark1 on 2007-10-13
In edgy when I added ntfs-3g it took much more cpu overhead for me than ntfs driver.  My ntfs was used on an ide hard disk drive and the ntrf-3g was on an usb hdd.  

Is ntfs-3g still more cpu intensive than ntfs?

---

### Post by MystaMax on 2007-10-13
Sorry guys. I wasn't implying that I had a 500GB flash drive. Its just a regular IDE drive in a USB enclosure. Didn't mean to confuse anyone.

For those that care, they do make flash drives [larger than 4GB]("http://en.wikipedia.org/wiki/USB_flash_drive#Future_developments"). Newegg.com sells [16GB flash drives]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2003240522+1309425474&name=16GB").

---

