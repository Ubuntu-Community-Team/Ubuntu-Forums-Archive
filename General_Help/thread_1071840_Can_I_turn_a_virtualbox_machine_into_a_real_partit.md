---
title: "Can I turn a virtualbox machine into a real partition?"
date: 2009-02-16
forum: General Help
---

### Post by mtgmutton on 2009-02-16
I have a WindowsXP virtualbox machine on  my Linux Mint box. I have recently decided to mod my Xbox360, which requires mounting the Xbox360's drive to the computer. Xplorer360 crashes,so I need to either make the virtual machine a real partition that is separately bootable, or find a replacement for Xplorer360 that is linux-friendly. The former seems much more likely. Can anyone help me?

---

### Post by caljohnsmith on 2009-02-16
I think probably the easiest way to transfer your VirtualBox OS to a partition would be to mount it, and then copy its entire file system to its new partition with "cp -ax" to preserve all the proper permissions/ownerships of all files. Most VirtualBox VDI files have just 3 sectors of VirtualBox header info at the beginning, and then the rest is the HDD image. So to mount a VDI file, you can usually do:
```
sudo losetup -f --show -o $((512*3)) ~/.VirtualBox/HardDisks/HDD_image.vdi
```
That will also return the loop device that the VDI file gets associated with, for example "/dev/loop0". And then to see the partitions in that image:
```
sudo fdisk -lu /dev/loop0
```
Using the above command, find the sector offset of the partition you want to mount, say for example the starting sector is 63, then do:
```
sudo mount -o loop,offset=$((512*[COLOR="Blue"]63[/COLOR])) /dev/loop0 /mnt
```
And that will mount your VirtualBox OS partition on /mnt. After that, it's just a matter of copying the file system to its new partition:
```
sudo cp -ax /mnt/* /path_to_mounted_destination_partition/
```
And lastly, if you do:
```
sudo blkid -c /dev/null
```
It will show you the UUID of your mounted VirtualBox partition, and you can transfer that UUID to the new partition with:
```
sudo tune2fs -U [COLOR="Blue"]<VirtualBox partition UUID>[/COLOR] /dev/[COLOR="Blue"]<new partition>[/COLOR]
```
You will probably have to modify /boot/grub/menu.lst and possibly /etc/fstab for the OS on the new partition, but that should be about all it takes. Let me know if you decide to give this method a try and how it goes.

---

### Post by mtgmutton on 2009-02-17
Thanks much, I will try this soon :)

---

### Post by mtgmutton on 2009-02-17
On this command...

 ```
sudo fdisk -lu /dev/loop0

Disk /dev/loop0: 32.2 GB, 32212376576 bytes
255 heads, 63 sectors/track, 3916 cylinders, total 62914798 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000016e

Disk /dev/loop0 doesn't contain a valid partition table
```

I'm not sure what the starting sector is... is it 63?

---

### Post by caljohnsmith on 2009-02-17
So did you mount your VDI file with the first losetup command that uses the 3 sector offset? If so, maybe the HDD image in the .vdi file starts at a different sector. How about posting the output of:
```
hexdump -C -n10000 [COLOR="Blue"]HDD_image.vdi[/COLOR] | grep -A1 "55 aa"
```
But replace HDD_image.vdi with your own .vdi image file.

---

### Post by mtgmutton on 2009-02-17
there was no output that I could see... nothing happened :(

---

### Post by caljohnsmith on 2009-02-17
You have to either give the path to your .vdi file, or you have to navigate to that directory using "cd" in the terminal. In other words, if your .vdi file is in your .VirtualBox directory, you might do something like:
```
hexdump -C -n10000 ~/.VirtualBox/HardDisks/[COLOR="Blue"]HDD_image.vdi[/COLOR] | grep -A1 "55 aa"
```
If you have problems, copy/paste exactly what you have in the terminal to your next post so I can see what you are doing.

---

### Post by mtgmutton on 2009-02-17
I listed the entire directory the first time, but nothing happened... so I tried again by cd-ing first, which produced the same results.

```
 hexdump -C -n10000 ~/.VirtualBox/VDI/WinXP.vdi | grep -A1 "55 aa"
```

---

### Post by caljohnsmith on 2009-02-17
OK, how about posting:
```
ls -l /home/evan/.VirtualBox/VDI
hexdump -C -n10000 /home/evan/.VirtualBox/VDI/WinXP.vdi
```

---

### Post by mtgmutton on 2009-02-17
ok for 

```
ls -l /home/evan/.VirtualBox/VDI

```

i got this:
```

total 31488164
-rw------- 1 evan evan 32212378112 2009-02-16 18:33 WinXP.vdi
```

and for 

```
hexdump -C -n10000 /home/evan/.VirtualBox/VDI/WinXP.vdi

```

i get.... it's really long... it takes up WAY more than one terminal window. is it possible to get the terminal to put command output into a txt file?

---

### Post by caljohnsmith on 2009-02-17
How about instead doing:
```
dd if=/home/evan/.VirtualBox/VDI/WinXP.vdi of=/home/evan/Desktop/WinXP.vdi.short count=20
```
That will create a "WinXP.vdi.short" file on your desktop; please attach that to your next post.

---

### Post by mtgmutton on 2009-02-17
ok that worked :D

I attached the file.

---

### Post by caljohnsmith on 2009-02-17
OK, I think I found the problem; you are still using the Innotek VirtualBox, and my directions were for the newer Sun version of VirtualBox. Can you upgrade your VirtualBox to the latest Sun version? If I remember correctly, when you upgrade you get the chance to convert your Innotek .vdi drive files to the newer Sun format .vdi files. That might be the best solution. You can download the latest VirtualBox by adding the VirtualBox repository to your sources.list as given by these directions:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Or you can simply download the .deb file from that same page and install it directly. If for some reason you really don't want to mess with upgrading VirtualBox, I would be willing to take a look one more time at your WinXP.vdi image to see if I can figure out how to mount it, but I will need to see more of the beginning sectors. To do that:
```
dd if=/home/evan/.VirtualBox/VDI/WinXP.vdi of=/home/evan/Desktop/WinXP.vdi.short count=1000
```
And then how about uploading that file to say [www.drop.io](www.drop.io) and give me the link (you can PM me with the link if you don't feel comfortable posting it in the forums).

---

### Post by drs305 on 2009-02-17
I have been following this thread and didn't want to butt in. I had the same "blank" result running the following from post 5 (Correct folder, etc): 
> hexdump -C -n10000 ... | grep -A1 "55 aa"
I *am* using Sun, 2.1.

If you don't mind looking at this and explaining why I get no results. It may help others using the Sun version. If you don't have the time or it will take a long explanation never mind as I don't want to hijack the thread. Thanks.

**Added: Yes, dynamic HDD**

---

### Post by caljohnsmith on 2009-02-17
Actually I'm really glad you popped in, drs305, and shared your results, because it made me realize that the issue is something else that I completely missed: the images I've been mounting are all static HDD .vdi images, and I just now tried with a VirtualBox dynamic HDD image and got the same results you did. So both you and mtgmutton are probably using a dynamically created HDD .vdi image, is that true? If so, I should have thought of that from the beginning. Sorry for leading us all on a bit of a round-about detour since I forgot you and/or mtgmutton might be using a dynamic disk. I'll have to look more closely at my dynamic HDD .vdi file to see if I can figure out how to mount it, and I'll let both of you know what I come up with. :)

---

### Post by mtgmutton on 2009-02-17
I'm not sure if I am using a dynamic disk, but I am also glad that drs305 posted :)

---

### Post by caljohnsmith on 2009-02-19
OK, I had a chance to experiment a little with a dynamic drive in VirtualBox, and here is what I came up with so far: I created a dynamic drive in VirtualBox, booted my gparted Live CD in VirtualBox, and formatted the dynamic drive with one NTFS partition. When I looked at the dynamic drive .vdi file, it was surprising similar to the static drive .vdi files I've been using in that it has a Master Boot Record (MBR) for the drive (as expected), and the MBR is located in the 3rd sector of the drive. So I used losetup to associate the .vdi file with a loop device similar to what I've been doing with a static drive, and I was able to use fdisk to read the partition table just fine. 

So I'm wondering if I went ahead and actually installed an OS like Windows to the NTFS partition on that drive through VirtualBox and "grew" my dynamic drive, how might the .vdi file change as far as where the MBR is? What I don't understand yet is why your .vdi drive files don't seem to have an MBR in them, at least in the first 20 sectors you posted (which could be the issue); that's what searching for the hex values "55 aa" is all about in those commands you ran, because "55 aa" is the MBR "signature". So I think it would help if both of you could tell me exactly how you created and set up your dynamic drive in VirtualBox, and the steps you took to install your respective OSes (Windows and Ubuntu Jaunty). Also, if you could send me the larger .vdi file that would be created from the command in post #13, mtgmutton, I could take a look to see if I can figure out what's going on.

---

### Post by mtgmutton on 2009-02-19
the little copy of the machine is here:

[http://drop.io/WinXPMachine](http://drop.io/WinXPMachine)

And as to how I created the virtual machine... I ran virtualbox, selected "new", and went through the process it requested. I asked for 30gb of space, 1gb of RAM, and it made the file... then it booted into the WindowsXP disc I had in, and I installed XP to the virtual machine. not sure if that helps.

---

### Post by drs305 on 2009-02-19
caljohnsmith,

I am using VirtualBox 2.1.4 (PUEL)
For my jaunty VM, the .vdi file is on a separate ext3 partition.
- Base Memory Size: 1024 MB
- Boot Hard Disk: New, Dynamically expanding storage, 8GB max.
- The CD image was originally the jaunty alpha .iso, which I mounted and installed in the VM. During the install at the partitioning phase I selected "use entire hard disk". Once it installed, I changed the CD Host drive from the .iso image to the empty CD player (/dev/scd0)
- I normally power off the VM rather than saving the machine state. When I start it, the VM goes through the standard ubuntu loading (orange progress bar) and ends at the Desktop. It no longer accesses the install image.
- Currently the Hard Disk IDE MAster is set to the Jaunty.vdi

Thanks.

---

### Post by moshazat on 2009-04-20
> **caljohnsmith said:**
> So did you mount your VDI file with the first losetup command that uses the 3 sector offset? If so, maybe the HDD image in the .vdi file starts at a different sector. How about posting the output of:
```
hexdump -C -n10000 [COLOR="Blue"]HDD_image.vdi[/COLOR] | grep -A1 "55 aa"
```
But replace HDD_image.vdi with your own .vdi image file.

hi
my output is this, so which one?

> @Comp:~/Desktop$ hexdump -C -n10000 se.vdi | grep -A1 "55 aa"
00002270  41 cd 13 58 72 16 81 fb  55 aa 75 10 f6 c1 01 74  |A..Xr...U.u....t|
00002280  0b 8a e0 88 56 24 c7 06  a1 06 eb 1e 88 66 04 bf  |....V$.......f..|
--
000023f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00002400  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|


---

### Post by caljohnsmith on 2009-04-20
Moshazat, according to the output of the hexdump command that you posted, it looks like the MBR starts at the 18th sector for your "se.vdi" HDD image file. That's not what I'm used to seeing with static .vdi images, but it might be perfectly valid anyway. How about posting the output of:
```
sudo losetup -f --show -o $((512*18)) se.vdi
sudo fdisk -lu /dev/loop0
```

---

### Post by Rizado on 2009-05-22
Thought I'd just throw some pointers to another webpage I found. Seems the headers are not always the same length but the command :
```
od -j344 -N4 -td4 image.vdi | awk 'NR==1{print $2;}'
``` will return the startingpoint.

This command is ripped directly of: [http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image](http://wiki.przemoc.net/tips/linux#mounting_partition_from_vdi_fixed-size_image) and this is not at all my doing.

Although I would probably just mount it using losetup and offset and sum up the offsets from fdisk with the one from the above command.

---

### Post by mtgmutton on 2009-05-22
I'm sorry, I have no idea what you just said... I think my IQ just dropped a few points from being so baffled :confused:

---

### Post by Rizado on 2009-05-23
> **mtgmutton said:**
> I'm sorry, I have no idea what you just said... I think my IQ just dropped a few points from being so baffled :confused:Oh I'm sorry =P 

Just follow the steps on the webpage I linked to. Make sure that you are using static size drives. Otherwise it won't work (It's the first command that outputs 1 or 2)

Also, I don't recall what offset I had yesterday but I think that it was different today. If that's so you'll have to rerun the offset command everytime you mount. The second offset, the one from drive start to first partition, should not change unless you reconfigure the partitions.

---

