---
title: "Another &quot;error 17&quot; problem from gparted..."
date: 2009-05-03
forum: General Help
---

### Post by herbig on 2009-05-03
So I was using gparted to format a USB, and I'm pretty sure I messed up the boot record of my hard disk.  I originally had a grub error 17 at startup, so I Googled around and found instructions to reinstall "lilo" using:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

What this did was that now when I boot is says no partition, or something similar (I'm on a live CD now and don't want to reboot...)

I also found the grub commands here:

sudo grub
root (hd0,0)
setup (hd0)

But when I get to the setup command, it says "Error 17: cannot mount selected partition"

Using the live CD, I can see all of my files as an "80.0 GB Media" drive.  I'm pretty sure I just need to restore the boot record or whatever, and not have to reformat the whole thing.. 


Some info:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a089a08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   156296384    78148161    b  W95 FAT32
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=156296322, Id= b
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
ubuntu@ubuntu:~$ 


Thanks for your help!

---

### Post by herbig on 2009-05-04
So I just restarted after trying some things, no changes, but here's what is says:

No partition active
No bootable devices


I also just noticed in the output of fdisk that my partition is fat32.  I'm pretty sure this is bad.. When I originally used gparted to format a USB, what I did was begin doing it on the hard disk, but canceled that when I realized what I was doing.  I'm pretty sure it can't change the file system, just perhaps what the boot thinks it is.. right?  Any way I can switch that back to a linux file system?

---

### Post by herbig on 2009-05-04
bizzump

Any help with this?  Should I be looking to just reformat and start over...

---

