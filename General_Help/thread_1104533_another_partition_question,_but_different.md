---
title: "another partition question, but different"
date: 2009-03-23
forum: General Help
---

### Post by PierreRussellStraddler on 2009-03-23
Hi everyone!

I have another partition question.

Originally I was a dual boot person.  Now I want to say buh-bye to windoze for ever and ever and ever and reclaim that partition space for Ubuntu!

in the process of making a dual boot machine, I (accidentally) created two ubuntu partitions.

I went to Gparted, and cleared the one old ubuntu partition (it is now "unallocated", and shrunk the old legacy partition.  

Here is what it looks like   


|--fat32 --|--unallocated---|--- /dev/sda5 ---|--linux-swap--|
  (3.26GB)    (20.79GB)         (12.62 GB)       (619.66 MB)


Partition  Filesystem   Mountpoint  Size      Used    Unused   Flags
/dev/sda1  -  fat32  -               3.26GB   981Kb   3.25GB   boot, Iba
unallocated  unallocated            20.79GB   ---      ---     
/dev/sda2     extended              13.22GB   ---      ---
  /dev/sda5   ext3        /         12.62GB   11.51GB  1.11GB
  /dev/sda6   linux-swap            619.66Mb  ---     ---

or said another way:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot  Start      End      Blocks   Id  System
/dev/sda1   *       1      425     3413781    c  W95 FAT32 (LBA)
/dev/sda2        3140     4865    13864095    5  Extended
/dev/sda5        3140     4786    13229496   83  Linux
/dev/sda6        4787     4865      634536   82  Linux swap / Solaris





I tried to use my ubuntu Live CD to try and make /dev/sda5 bigger--make it go into the 20.79 unallocated space, but it wouldn't let me unmount /dev/sda5, and so I couldn't make /dev/sda5 any bigger.

While I would ideally like to have one gigantic partition for ubuntu, I am worried about trying to move (or remove) the 'boot' from the fat32 /dev/sda1--and would just assume leave it as it is.  If however that is an irrational fear, please don't hesitate to tell me so.

In sum, at the very least, I am trying to achieve this:

|--fat32 [with boot]--|--gigantic ubuntu partion--|--larger linux-swap--|

but was unable to do so, even using Gparted on a liveCD.

Any help would make pierre russell straddler most appreciative!

thanks in advance

:)

(p.s. if anyone can tell me how to take a screen shot, I'll happily post a picture of my gparted screen.)

---

### Post by jo4hnc on 2009-03-23
I can help with the screen shot. Just hit alt Prntscn on your keyboard. You can either save it to the clipboard or save it to your desktop. It'll probably save as a .png file.

---

