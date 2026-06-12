---
title: "Installing 64 - wipe whole drive or single partition?"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by Johnny K on 2007-06-12
The Dellbuntu's ship with 6 partitions. So my question is...

When I install Ubuntu 64, should I wipe the whole drive, or just put the OS on the main partition?

---

### Post by tgm4883 on 2007-06-12
Well, what are the different partitions?

---

### Post by woncothesane on 2007-06-12
How important is the dell diagnostic partition?

Maybe resize the dellbuntu / and create your partition(s) for 64 bit and dual boot.
You could delete the factory partitions later if you don't need or want them.

---

### Post by Johnny K on 2007-06-13
> **tgm4883 said:**
> Well, what are the different partitions?

```
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

I'm not really sure what each partition is for. What's the worst that would happen if I just wiped the whole disk? Are any of Dell's partitions really that important?

---

### Post by camarojones on 2007-06-13
> **Johnny K said:**
> ```
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

I'm not really sure what each partition is for. What's the worst that would happen if I just wiped the whole disk? Are any of Dell's partitions really that important?


1 is to boot.
2 is restore
3 is diagnotics
4 is extended for 5 and 6
  5 linux
  6 swap

I already wiped everything and reloaded. works just fine.

---

