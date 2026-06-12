---
title: "No Hard Drive Found on Prepare Partitions"
date: 2009-02-14
forum: General Help
---

### Post by twisted_tim21 on 2009-02-14
Hello, I'm new at Ubuntu and I'm really interested in installing it, however I cannot prepare a partition because ubuntu cannot find the hard drive...

[http://www.flickr.com/photos/31609916@N05/3278850787/](http://www.flickr.com/photos/31609916@N05/3278850787/)

there is what i am seeing

My hard drive is SATA Maxtor

---

### Post by frklin on 2009-02-14
Run in terminal ```
sudo fdisk -l
```

---

### Post by 2hot6ft2 on 2009-02-14
> **frklin said:**
> Run in terminal ```
sudo fdisk -l
```
The terminal is located here in the menus.
Applications>Accessories>Terminal

---

### Post by twisted_tim21 on 2009-02-14
Ok I put it in the terminal.. then what?

---

### Post by k3rnelmustard on 2009-02-14
paste what the output was here.

---

### Post by twisted_tim21 on 2009-02-14
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x115e115d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 8019 MB, 8019509248 bytes
175 heads, 32 sectors/track, 2796 cylinders
Units = cylinders of 5600 * 512 = 2867200 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2797     7831535+   c  W95 FAT32 (LBA)

---

### Post by k3rnelmustard on 2009-02-14
So, linux recognizes your hard drives.  That's good news.  Go ahead and fire up gparted in the livecd, it's probably in accessories or system or something like that.  Once you're in there, put the drop down in the upper right on /dev/sda.  Then you should see the sda1 windows partition there.  Just click on, select resize, then pick a size that is just slightly larger (1 GB or so) than windows is already taking up.  Once that's done, just leave the empty, unpartitioned space at the end of the drive and try the installer again.

---

### Post by twisted_tim21 on 2009-02-14
what should the file system be?

ext
linux-swap
unformatted?

---

### Post by twisted_tim21 on 2009-02-14
[http://www.flickr.com/photos/31609916@N05/3279784456/](http://www.flickr.com/photos/31609916@N05/3279784456/)

ok this is what i see but still no hard drive in the installation

---

### Post by caljohnsmith on 2009-02-14
When you run the Ubuntu installer, which partition option are you using? Are you using "Guided - use free space", "Guided - use entire disk", or the "manual" partition option? Also, are you using an Intrepid 8.10 Live CD or a previous version?

---

### Post by twisted_tim21 on 2009-02-14
> **caljohnsmith said:**
> When you run the Ubuntu installer, which partition option are you using? Are you using "Guided - use free space", "Guided - use entire disk", or the "manual" partition option? Also, are you using an Intrepid 8.10 Live CD or a previous version?

I'm using ubuntu 8.10 intrepid. 

 I cannot find guided- use free space on the installer or the manual... i've only seen it when i put in my 1.0 gb flash drive and i don't think thats enough to install ubuntu

---

### Post by k3rnelmustard on 2009-02-15
That's really weird.  Well, rather than have that partition be ext2 in gparted try just making it unpartitioned space, and see if the installer can see it then?

---

### Post by pizzavesel on 2010-01-29
Hllo ther i seem to have the same probleme whit my pc, the hdd is clean and when i right the sudo fdisk -l i get this:

Disk /dev/sda: 320.1GB 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinder
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92443d2b

     Device    Boot    Start      End          Blocks    Id   System
/dev/sda1       *            1  12902   103635283+   7   HPFS/NTFS
/dev/sda2                     1  38913   208933357+   7   HPFS/NTFS


And the same thing it donsen't show in the Prepare Partitions manager whit ubuntu 9.10 desktop x64 bits paltfom amd x 64 motehrboard asus m2n-mx-se hdd WD 320GB sata2. The cd pases the test .


The drive is clean and formatet i'v tryde something whit swap but it dose the same thing, i'm new in Linux, but i'm tired of win..... crashes.

---

### Post by k3rnelmustard on 2010-01-29
I would appear that your drive isn't clean, as you have two partitions listed.  In the GUI installer can you choose the option guided - use entire disk?  Which option are you trying?

---

### Post by pizzavesel on 2010-01-29
Problem solved i used the Ubuntu 9.10 Alternate amd x 64 version and it works like a charm. And whit the other version i tryde allmoste evry kinde of partition even 1 lager partiton in all the ways.

---

