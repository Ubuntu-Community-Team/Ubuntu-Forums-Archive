---
title: "having trouble entering commands in menu.lst"
date: 2009-06-21
forum: General Help
---

### Post by wanderingarticfox on 2009-06-21
I lost connection yesterday but have recieved a reply today [see installation thread Installed 9.04 and lost HDD 6-20-09]. I am trying to get a grip on how to enter the data after entering the menu.lst for grub. I know I have to use the # sign and understand that the info provided is a line by line entry but I am a neebie and cannot understand how to do this](*,)  I tried at the end of cat /boot/grub/menu.lst but after the display I am at my 'name' with a prompt.  I believe that cat means catalogue so I'm thinking it is an information and data page.
I realize that there is a lot of information via community and even here in forums but my learning curve is steep and I'm trying to recover my windows HDD. Any help on this will be very appreciated and you can post respond here or to the thread from yesterday.

---

### Post by michy99 on 2009-06-21
To make changes to menu.lst, you need to open it in a text editor. Since you will need root permissions to save the edited file, you need to open it as root. In a terminal, enter```
gksudo gedit /boot/grub/menu.lst
```This will let you make changes and save the file.

Make sure you know what you are doing before making changes.

---

### Post by wanderingarticfox on 2009-06-21
> **michy99 said:**
> To make changes to menu.lst, you need to open it in a text editor. Since you will need root permissions to save the edited file, you need to open it as root. In a terminal, enter```
gksudo gedit /boot/grub/menu.lst
```This will let you make changes and save the file.

Make sure you know what you are doing before making changes.

I have a more intensive thread in the installations and upgrades, I just posted this result there too.

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/memtest86+.bin
quiet

title           Windows
rootnoverify    (hd0,0)
makeactive
chainloader     +1
### END DEBIAN AUTOMAGIC KERNELS LIST


I'm not sure if I'm doing this in the proper place but I still do not see the Windows XP option in the GRUB menu at start-up or restart. And yes I press the 'Esc' key to view the list. I know windows is still there because it crashed my old single core last night while trying to install KCalc and another program. I forgot that it was time for it to run mant. functions  on Sun AM and I need to get in there and change things.](*,)

Now I have to learn about dpkg --configure -a to fix that:confused:

---

### Post by merlinus on 2009-06-21
Move this:

title           Windows
rootnoverify    (hd0,0)
makeactive
chainloader     +1

below this line:

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by wanderingarticfox on 2009-06-21
Sorry about double post; still no joy:confused:


title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0f930882-7220-4fe4-b488-5bce06e8a8ac ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0f930882-7220-4fe4-b488-5bce06e8a8ac
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows
rootnoverify    (hd0,0)
makeactive
chainloader     +1


Do I need to specify Windows XP ?:confused:

---

### Post by merlinus on 2009-06-21
No.  The entry is correct, based upon the information you have given.

At this point, I see two options for at least booting into xp.  One is supergrub, and the other is to use your xp install cd, select recovery, and then fixmbr.

Info on supergrub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can always reinstall grub to double-boot, if need be.

---

### Post by wanderingarticfox on 2009-06-21
OK Thx Merlinus; I'll seek help in Super GRUB forums. I think I might not have the skills for the windows recovery since I have only done it once with just one HDD. I'm guesssing I could unplug the second drive and try but it wipes out all data  and if that's the case I think my time is better spent really learning Ubuntu because I really want to fire microsoft before I build a new system in Sept.. Thanks for your help and look for me in the near future, I seem to learn by breaking:D

---

### Post by wanderingarticfox on 2009-06-21
I went back into the Gnome Partition editor and looked in my book on8.10 and found a note concerning Hard Drive Names on Linux Systems saying that EIDE/ATA use to be in the form /dev/hdX but that they are now /dev/sdX.

Like I've said before I really was not meaning to be at page 1000+ yet in this book so I have not even learned screen shots and the Gnome Pat. Editor would not allow me to highlight >copy>paste so I copied the information from there into Tomboy notes and this is what I get:

GParted via Gnome

ATA ST340016A origional Compaq HDD

/dev/sda1   ntfs                 33.37GB           flag>>boot

unallocated                          1.85MB

/dev/sda2    extended           3.90GB         flag>>lba

/dev/sda5   fat32    system_sav    3.90GB    3.43GB used           

                                             482.45MB free

there is a caution triangle after  /dev/sda1 


ATA Maxtor 33073H3  

/dev/sdb1  ext3  mounted /  27.4GB  2.9GB used  24.5GB free

/dev/sdb2   extended       1.22GB

/dev/sdb5   linux-swap     1.22GB

I also posted at Super Grub Forum but no answer as of yet.
I did notice an command entry that had a map  (hdX) (hdY) before the rootnoverify
makeactive
chainloader  +1

then at the end another line that just said 'boot'

If someone understands this please help, once I can get back to dual boot I can return to the page by page learning I was trying to do.](*,)](*,)

reshowing fdisk listing:

articfox@PolarWatcher:~$ sudo fdisk -l
[sudo] password for articfox: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4356    34987648+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4356        4865     4088543    f  W95 Ext'd (LBA)
/dev/sda5            4357        4865     4088542+   b  W95 FAT32

Disk /dev/sdb: 30.7 GB, 30736613376 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09aae0b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3577    28732221   83  Linux
/dev/sdb2            3578        3736     1277167+   5  Extended
/dev/sdb5            3578        3736     1277136   82  Linux swap / Solaris
articfox@PolarWatcher:~$ 

Thought that might help too.

---

### Post by merlinus on 2009-06-21
Here is excellent info on using supergrub:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")

Since windows is on (hd0,0) --  /dev/sda1, if you are booting from that hdd first you do not need map statements.

---

### Post by wanderingarticfox on 2009-06-21
Thank You Merlinus; I took the time to make sure I understood the apt's in Super GRUB and it worked with the use of two applications.
Thank you to everyone who helped.  Super Grub was the answer for this issue.:D

---

### Post by merlinus on 2009-06-22
Excellent news!  Good on you for hanging in there, and happy ubuntuing.

---

