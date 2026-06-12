---
title: "Dell Poweredge 2950 Raid 5"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by savee on 2008-04-25
Ok here is my specs

Quad Core Xeon E5405 Processor2x6MB Cache, 2.0GHz, 1333MHz FSB, 
Quad Core Xeon E5405 Processor2x6MB Cache, 2.0GHz, 1333MHz FSB, 
4GB 667MHz (4X1GB), Dual Ranked Fully Buffered DIMMs 
Riser with 3 PCIe Slots for PowerEdge 2950 
PERC6i SAS RAID Controller, 2x4 Connectors, Int, PCIe, 256MB 
Two (2) Integrated Broadcom NetXtreme II 5708 Gigabit NICsTOE  
24X IDE CD-RW/DVD ROM Drive
1x6 Backplane for 3.5-inch Hard Drives (311-7936)
Integrated SAS/SATA RAID 5, PERC 6/i Integrated (341-5723)
Redundant Power Supply with Dual Cords 
4-1TB 7.2K RPM Universal SATA 3Gbps 3.5-in HotPlug Hard Drive 

As you can see I am using the PERC6e Raid controller.
I created one virtual disk through the controller. I made it raid 5 and it comes up to be 3 TB. I go through the installation of 7.10 server edition and 8.4 server edition. Both are a complete failure. Whenever I get to the point of installing Grub or LILO. A fatal error occurs. But not always. I tried to install LILO  and it was successful. When I reboot, Lilo begins to load and then just stops during the boot. 

I have tried many different things. Installing on 2 different raid drives. One is good and the other is bad. This time I installed 7.10 on one drive and 8.4 on the other, just to see if i could get Grub to install on one of the platforms. Works! Restart. Grub loads. I see my 8.4 on my other raid, load, ERROR, Something about a bad directory.

 I Just want to be able to install 8.4 or 7.10 to my whole Virtual Disk (3TB). Is there anything advice you guys could provide me with. If i have to i'll create 2 VD's and Do a small one and a large raid.

Thanks

---

### Post by barichardson5727 on 2008-04-26
I cant think of a single reason why you would want your OS installed onto a single 3Tb volume anyway. I cant see it causing anything but problems in the long run. You should install your OS onto a smaller, more manageable VD and you data on the remaining space as a seperate VD. 

Create you new VDs in the perc bios. When you install ubuntu this time just partition out your smaller VD with the OS and leave your remaining space unused. You can worry about setting that up the large partition after the install completes successfully. 
Leaving the large disk unused should allow you boot without the errors you are getting now. When you are able to boot into the OS you can then partition your remaining VD. Most versions of linux I have come across run into problems with partitions over 1.2Tb using the disk-druid during install. I normally just partiton them myself after linux has been installed. 

When it comes time to partition the large VD you will have to use parted because fdisk cannot large partitions (I think the limit is somewhere around 1.2Tb). You should use parted and set the partition type to gpt. This will allow you to use all of you space. 

When you put a file system on your newly created partition you will need to modify the block size since the default will not allow large partitions. Since you have ~3Tb you should be fine with a 4MB block size. when creating the filesystem this is specified with the "-b" switch.
example: mke2fs -j -b 4096 /dev/sdb1

Also, normally when I setup my fstab on large partitons I use 0 0 for the last two sections. This keeps you from having to wait hours when the server wants to fsck at bootup.

---

### Post by savee on 2008-04-27
I must have forgotten to mention that. I did install on a 30gb VD but then could not see the other VD. I fully support partitioning the OS on a smaller, more manageable drive. What can I say? I was desprate...I cannot remember the program I was using to search for it. I believe it was the built in Partitioner through Ubuntu. I did try the install again over the weekend. First I tried installing Grub to a floppy (lol) , that was a no go. Then I installed LILO to
the OS and not the master boot record. It worked. ( I have no experience with Lilo) I rebooted. Everything came up great. So I will proably redo everything again and try to get my OS on a smaller drive, but in the mean time I was trying to get a GUI on the 8.4 server install. I need this, for there are many other people that are going to be VNC to the server. More issues arrived. I would do the common : Sudo apt-get install ubuntu-desktop. Could not find Ubuntu-desktop. I have did this before on 7.10. The above sudo command might not be the correct command but my brain is fried so bare with me. 

Any Ideas as to why I cannot get a GUI on ubuntu 8.4 server?

---

### Post by savee on 2008-04-27
By the way Thank you for the Response!!

---

### Post by barichardson5727 on 2008-04-29
could you post output from running "sudo fdisk -l" so I can see what ubuntu thinks your existing partition table looks like. You should get something like this:
```
brad@rasengan:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       38913   312464250   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3499.9 GB, 3499998838784 bytes
255 heads, 63 sectors/track, 425517 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483647+  ee  EFI GPT

```

I haven't actually tried using 8.04 server yet so I don't really have an answer for the gui installation, but in the past I normally just ran "sudo apt-get install ubuntu-desktop" and it worked without any problems. Possibly those packages are listed on a repository that you have disabled in /etc/apt/sources.list.

---

