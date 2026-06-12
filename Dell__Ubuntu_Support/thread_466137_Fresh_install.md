---
title: "Fresh install"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by Johnny K on 2007-06-06
I'm going to install 64 Ubuntu once I get my Dellbuntu (it ships with 32). benanzo mentioned that his Dellbuntu shipped with 6 partitions...

```
ben@dell:~$ sudo parted
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16             
 2      49.4MB  2204MB  2155MB  primary   fat32             
 3      2204MB  2410MB  206MB   primary   ext3         boot 
 4      2410MB  500GB   498GB   extended               lba  
 5      2410MB  5059MB  2649MB  logical   linux-swap        
 6      5059MB  500GB   495GB   logical   ext3              

(parted)
```

So I was wondering, when I reinstall Ubuntu, would there be anything wrong with wiping the whole disk, or would I want to have something similar to the above?

---

### Post by bherring on 2007-06-06
So I convinced my girlfriend to order one of these.  She ordered the E1505n and got it last night.  I noticed some odd things.

The partitioning scheme has some space set aside for the OS installer.  I haven't figured out how to remove the software and place it on a bootable DVD, but that would seem optimal to me.

Also, after a security upgrade of the kernal, grub configuration was pointing to the wrong partition.  Once I figured that out and corrected it, the kernal was missing some essential modules for sound and networking.

I was wondering if anyone else had experienced this?

---

### Post by starcannon on 2007-08-30
> **bherring said:**
> So I convinced my girlfriend to order one of these.  She ordered the E1505n and got it last night.  I noticed some odd things.

The partitioning scheme has some space set aside for the OS installer.  I haven't figured out how to remove the software and place it on a bootable DVD, but that would seem optimal to me.

Also, after a security upgrade of the kernal, grub configuration was pointing to the wrong partition.  Once I figured that out and corrected it, the kernal was missing some essential modules for sound and networking.

I was wondering if anyone else had experienced this?

I want to do the same thing with the OS partition on my 1420n have you found an answer yet?

---

### Post by vanden12 on 2007-08-30
I am very sure than you can resize these...

Just install it over the boot drive....

---

