---
title: "Some questions about partitionning and files storage"
date: 2009-04-27
forum: General Help
---

### Post by neo tenshi on 2009-04-27
Hi there

First of all, I hope I'm in the right forum (didn't really know how to post this), and I hope this topic hasn't been discussed too much already.

So, here's my "problem" :
I'm using ubuntu for quite a while now, dual-booting with Windows Vista (just in case), and with time passing by I've accumulated kind of a number of files, and my Ubuntu partitions got full, so, I tried resizing my partitions as said in the documentation. Reducing Windows partition went well (I couldn't reduce as much as I wished but that was to be expected), but I haven't been able to extend Ubuntu partitions. I booted from a liveCD and so on, but the only thing gparted allows me to do is *reduce* de partitions (even using root account). So, that surprised me given that all the space freed by windows in contiguous Linux partitions.
Here's my partitions table :

```
/dev/sda1   Windows (primary)   about 350 GB   NTFS
*** Free space   around 70 GB ***
/dev/sda2   extended partition
   /dev/sda5   Linux root (logical)   8 GB   ext3
   /dev/sda6   Linux swap   1 GB
   /dev/sda7   Linux home   18 GB   ext3
/dev/sda4   Windows recovery
```I tried extending the home partition, the root partition and the extended partition, but none of these worked. Any idea of the causes ?


By the way, another thing I wanted to ask to you is : how would you dispatch your files between the different partitions ? I know it's something "personnal" but I'm kinda perplexed on how to manage my files.
I have an external HDD of ~150 GB and a regular disk drive partitionned as above. There are GB's of files that I wanna keep safe, but because these *are* GB's of them I can't keep them on both drives, but I don't know wheter it's better (in terms of safety and convenientness) to store them on the internal HDD or the external one ... (note that the external one is FAT32, so no 4GB+ files on it). At the moment, the big files (DVD images, anime, videos, and so on) are on the Windows partition with symlinks in my ~ folder, the smaller ones are in my ~ folder and/or my external HDD and the "precious" ones are on both. So, some questions I wanted to ask you include :


[LIST=1]
[*]Is it safer to store files on an external or regular HDD ?
[*]Is it okay to use my Windows partition mainly as a storage partition ?
[*]How much space would you allow to Ubuntu (/ and /home) given that I can only free 70 GB out of 500 ? (f*** Windows)
[/LIST]

Thanks in advance
Have a nice day

---

### Post by ivanvajar on 2009-04-27
You can create partition to store your data on it. I have 2 NTFS partitions for data storage only. You are unable to resize/extend your home partition because your home partition is not next to unallocated space.

---

### Post by neo tenshi on 2009-04-27
That's what I guessed but I couldn't move/extend my root partition either (and this one is next the unallocated space)

Creating data partitions is also something I thought of (the home partition has been created for this purpose), but I have free space on my Windows partition (and windows doesn't allow me to reduce it), so I better fill this one first ... (creating yet another partition would result in having 6 partitions of average size, which isn't that convenient/usefull)

---

