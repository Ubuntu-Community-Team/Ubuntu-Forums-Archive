---
title: "cpu history goes 100% on using file system"
date: 2009-07-08
forum: Desktop Environments
---

### Post by satish_j on 2009-07-08
Everytime i access the file system,CPU history jumps to 100% from 25% and stays there for 20-25 sec before returning back to again 25%.During this time,i cannot even access the desktop.
Situation is worse with ntfs partitions of windows.I have a music folder in ntfs partition.OPening it takes around 1 min,during which time,cpu is at 100% and the system is not at all usable.
I also observed that during this time,swap usage is 0% and there is no significant increase in memory usage.
Can anyone help me out with this..Iam using nautilus as file browser.can this be related to nautilus in anyway??

---

### Post by HOLY COW on 2009-07-08
I had a similar issue , wherein my entire laptop was sluggish to no end (not just Nautilus). Turns out, i had a faulty install due to an even faultier cd-rom drive (which presumably did a bad job on installing/writing my Ubuntu 9.04). So try reinstalling your OS again? :(

---

### Post by prshah on 2009-07-08
> **satish_j said:**
> Everytime i access the file system,CPU history jumps to 100% from 25% and stays there for 20-25 sec before returning back to again 25%.Situation is worse with ntfs partitions of windows.

25% for idling is too much. What is your system configuration?

Do you have DMA access enabled for your hard disk drive (I doubt it). Open a terminal (Applications-Accessories-Terminal) and give the below commands and post back the output```
dmesg | grep -i dma
dmesg | grep -i drdy
dmesg | grep -i exception\|emask
``` These will give clues as to what problems, if any, are there.

---

### Post by satish_j on 2009-07-09
> **prshah said:**
> 
Do you have DMA access enabled for your hard disk drive (I doubt it). Open a terminal (Applications-Accessories-Terminal) and give the below commands and post back the output```
dmesg | grep -i dma
dmesg | grep -i drdy
``` These will give clues as to what problems, if any, are there.

I have already run the below command:
sudo hdparm /dev/sda6
and got the err as "Inappropriate ioctl for device'
I googled about it and found that it can be due to kernel not supporting motherboard chipset.iam using intel 845 series chipset.
If that is not the way to check DMA settings,I will post the output of your commands today evening when i 
reach home.

---

### Post by prshah on 2009-07-09
> **satish_j said:**
> I have already run the below command:
sudo hdparm /dev/sda6

You cannot use hdparm on /dev/[color=red]sda6[/color]; you can only use it on /dev/[color=blue]sda[/color] hdparm works with the hard drive (sda), not a partition (sda6).

In any case, checking dmesg is a far less invasive method. Please note that I've added a third command.

Also, I do not think you can use hdparm to set parameters for a scsi device; sda (instead of hda in some other distributions) indicates the usage of a (virtual) scsi subsystem. DISCLAIMER: I'm not too sure about this.

---

### Post by anchorschmidt on 2009-07-09
Can you check the processes and see what's taking up all that CPU. Do you have a swap partition?

---

### Post by satish_j on 2009-07-09
> **anchorschmidt said:**
> Can you check the processes and see what's taking up all that CPU. Do you have a swap partition?

nautilus is using all that CPU..regarding swap partition,i have no idea whether i have a swap partition.Although system monitor displays the swap usage as 0.Can you tell me how to check for swap partition??

---

### Post by prshah on 2009-07-09
> **satish_j said:**
> .Can you tell me how to check for swap partition??

```
free -m
``` will list available, used and free swap.

---

### Post by satish_j on 2009-07-09
I came to know that hdparm can only be used with /dev/hdx drives i.e IDE devices only.
Iam also using IDE devices,then why my system shows /dev/sdx as the names of drives instead of /dev/hdx.
(Now,this is getting more confusing..)

---

### Post by prshah on 2009-07-09
> **satish_j said:**
> I came to know that hdparm can only be used with /dev/hdx drives i.e IDE devices only.
Iam also using IDE devices,then why my system shows /dev/sdx as the names of drives instead of /dev/hdx.

The latest libata (used to access modern drives) encapsulates IDE operations in a "virtual" scsi subsystem.

To understand this, you must have some background knowledge of SCSI and DMA architecture.

SCSI came along before DMA; it stands for Small Computer System Interface, and is in essence an alternate processor for various I/O tasks so that the main processor is freed from handling I/O. 

DMA is a cheaper technology that does something similar; it hands off I/O intensive tasks (though it refers to IDE I/O only) to inbuilt processors in the hard drive.

So I assume that rather than have duplication of effort, the newer libata simply treats the IDE drives as a SCSI subsystem and hence the "sd"a.

Can you post dmesg output as requested?

---

### Post by satish_j on 2009-07-09
> **prshah said:**
> You cannot use hdparm on /dev/[color=red]sda6[/color]; you can only use it on /dev/[color=blue]sda[/color] hdparm works with the hard drive (sda), not a partition (sda6).

In any case, checking dmesg is a far less invasive method. Please note that I've added a third command.

I tried with /dev/sda and got the same result:
```

satish@TITAN:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 4870/255/63, sectors = 78242976, start = 0
satish@TITAN:~$ 

```
Also,out of the 3 commands you specified,only first one gave the output as follows:Rest did not give any output
```

satish@TITAN:~$ dmesg |grep -i dma
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[   29.850435] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   29.850439] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   30.021390] ata1.00: ATA-7: SAMSUNG SP0411N, TW100-11, max UDMA/100
[   30.038111] ata1.01: ATA-7: WDC WD1600AABB-22PUA0, 00.07H00, max UDMA/100
[   30.045364] ata1.00: configured for UDMA/100
[   30.054041] ata1.01: configured for UDMA/100
[   30.364678] ata2.00: ATAPI: HL-DT-ST GCE-8526B, 1.03, max UDMA/33
[   30.536122] ata2.00: configured for UDMA/33
satish@TITAN:~$ dmesg |grep -i drdy
satish@TITAN:~$ dmesg |grep -i exception\|emask
satish@TITAN:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           749        684         64          0         15        277
-/+ buffers/cache:        391        357
Swap:          588         37        550
satish@TITAN:~$ 

```
Awaiting your response..

---

### Post by prshah on 2009-07-09
> **satish_j said:**
> 
Also,out of the 3 commands you specified,only first one gave the output as follows:Rest did not give any output


The fact that the other 2 commands gave no output is good; it has found no errors to flag.

I can't really think of anything else.

---

### Post by satish_j on 2009-07-09
omg..what should i do now??prob is still there and it is causing a lot of frustation.have to wait for 1-2 min for folder to open..
Do you think i should try re-compiling the kernel??will it be of any help?

---

### Post by satish_j on 2009-07-10
[SIZE="2"]I ran 'hdparm -tT /dev/sda' and the result i got was pretty good.
It showed 400MB/sec for buffer-cache reads and 65MB/sec for buffered disk-reads.
Actually,I am dual-booting XP from same drive and i have installed 'Intel application accelerator' in XP,which enables DMA automatically on all drives.
So,i guess that DMA is already enabled on my drives as XP is running super-fast.But,at the same time,i cannot understand what makes Ubuntu to perform in a sluggish way.[/SIZE]
[SIZE="1"]*I think i should start the poll now:How much time does it take to open a 4GB folder(on windows partition) from your linux distro*[/SIZE]

---

### Post by satish_j on 2009-07-11
VERY VERY HAPPY TODAY.....
My problem is resolved thanks to the post by Handaxe in below thread:
[http://ubuntuforums.org/showthread.php?t=470947](http://ubuntuforums.org/showthread.php?t=470947)
It was because of 'ASsistive technology' being enabled by default that was causing issues with nautilus.Also,it is a known bug in nautilus.
Cant understand how can they keep default level as ON for a technology that is causing a lot of performance issues?
I was looking for solution to this problem for last 2 months.Finally got it.MY days of frustration with ubuntu are finally over.Iam going to bid final goodbye to XP.From now on,i will be using Ubuntu and only ubuntu on my home PC.
Cheers......

---

