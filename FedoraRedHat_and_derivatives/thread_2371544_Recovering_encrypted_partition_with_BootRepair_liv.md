---
title: "Recovering encrypted partition with BootRepair livecd"
date: 2017-09-15
forum: Fedora/RedHat and derivatives
---

### Post by hwdualstudent on 2017-09-15
[SIZE=3]I am using a BootRepair live cd to fix a problem I was having.
[SUB](This BootRepair live cd seems to be built off of ubuntu, so that's why I tried this forum. Sorry if this isn't the right place to ask. I'll ask another forum instead if requested)
[/SUB]
**The problem: **My laptop should have a dual boot system. But it only boots to windows upon startup. The disk manager now recognizes that another partition exists (the partition with my other operating system), however I can't figure out how to boot from it. BootRepair says the partition is encrypted, so this is supposedly preventing me from fixing the dual boot system with BootRepair.

**How this happened**: My laptop used to run windows 7 and fedora 22[SUB] (I'll move this to a fedora forum if asked). [/SUB]But I ran out of storage space on Fedora. I used a gpartition livecd to try shrinking the windows partition and expanding expanding fedora one. [SIZE=2]But between those two partitions was a 500mb partition that didn't seem important, so I removed it since the new unallocated space needed to be next to the fedora partition for me to use it.[/SIZE][/SIZE] [SIZE=3]I think this deleted my partition table or destroyed my boot sector, because I was booted to grub. I used used a BootRepair live cd, and I was able to boot back into windows. But the disk manager thought I just had one big partiton. After using TestDisk, the disk manager now recognized the seperate partitions, My fedora  partition was there, but for some reason I couldn't boot from it.
[B]
What I tried:[/B] I figured I could use BootRepair to help recover this partition and make it usable and bootable again. But the partition was encrypted, so things got confusing.

At first, BootRepair generated this report [http://paste.ubuntu.com/25541022/](http://paste.ubuntu.com/25541022/)[/SIZE]
This report told me I should decrypt the partition, but I couldn't find a clear answer on how to safely do that.
But from the livecd file manager, I was able to open the "lost" partition. At first it said 37gb (the new expanded size). When I entered my fedora password, I could actually see all the files that I thought were lost. However the description changed from "37gb" to "14gb" (the old size before I expanded it). And when I ran BootRepair again, it gave me a new report [http://paste.ubuntu.com/25542160/](http://paste.ubuntu.com/25542160/)

[SIZE=3]So where do I go from here? I'm not familiar with the operating system this livecd uses [SUB][SIZE=2](which I assume is ubuntu)[/SIZE][/SUB]. [/SIZE]So how can I fix this encrypted partition?

---

### Post by oldfred on 2017-09-15
Moved to Fedora sub-forum.

I do not know LVM nor encryption, but to use with Ubuntu you have to add lvm2 & cryptsetup drivers.

 To get Ubuntu to see different encrypted install (change to your partition):
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sda5 my-crypt

 sudo pvdisplay
sudo lvdisplay
mount
sudo vgscan --mknodes
sudo vgchange -ay 



First part is on mounting, rest is resizing after mount.

 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by hwdualstudent on 2017-09-15
Wow! That definitely helped a little bit. I ran all those commands then used Boot Repair. Boot repair actually recognized that fedora was installed on one of those partitions and tried to fix it. Before it finished, it gave this error message: > Please enable a repository containing the [linux-generic] packages in the software sources of Fedora release 22 (Twenty (mapper/fedora-root). Then try again.
I'm not sure what that means. But I'll have to check if I can dual boot now. I'd even be happy if windows msconfig just recognized the other operationg system.

---

### Post by hwdualstudent on 2017-09-15
Ah. Okay, I found an old forum topic about this exact problem. You even answered it. [https://ubuntuforums.org/showthread.php?t=2274963](https://ubuntuforums.org/showthread.php?t=2274963)
So it looks like I'll be reinstalling the operating system again. I figured I was going to end up doing that anyways since the resizing didn't work.

---

### Post by oldfred on 2017-09-15
Linux does not see Linux partitions, so now sure what you want from Windows.
And not other system should see encrypted partitions unless you specifically mount them and un-encrypt them.

Fedora uses LVM by default. With Ubuntu it is an option for advanced users. 
But if you want encryption  with Ubuntu you have to use LVM.

---

