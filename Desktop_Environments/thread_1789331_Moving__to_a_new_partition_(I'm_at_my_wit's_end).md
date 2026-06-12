---
title: "Moving / to a new partition (I'm at my wit's end)"
date: 2011-06-23
forum: Desktop Environments
---

### Post by Silveri on 2011-06-23
I'm running Kubuntu 10.04 LTS and had a partition system where / was a primary partition of 8 GB size and /home was on a separate, much larger extended partition, where the swap was also located. Unfortunately /usr was also on the primary partition, which is now full and I'm struggling to keep the system together.

I then decided on a simple/-ish solution, of "Hey! If I buy a 30 GB SSD-drive and move my root directory and swap there and have a system then that's heck of a lot faster!"

I did not want to install linux again, to preserve the data in the /usr, since I do have some software that I've paid for and wouldn't wish to reinstall everything. Grantedly, this will be my "if all else fails" option.

I cloned my root partition with clonezilla to the SSD drive - from a primary partition in ext4 format to an extended partition in ext4 format (so as I might have the option of resizing the partition later on if required) on the SSD drive. After a couple of initial hiccups, this went well and I can mount the partition fine. As my fstab was automatically created and used UUID:s (and CloneZilla also cloned the UUID, as I soon found out after reboot - it also had problems stating used drive space, but gparted fixed that problem promptly), I had to change the UUID on the new partition.

No problems again.

So. I knew I had to then install grub on the boot sector of the SSD drive (done without problems), edit the fstab to match the new boot sector.

So, I checked the new UUID with blkid and edited fstab (for both the old boot partition and the new one, to make it on the safe side). I did it first in the UUID format, and lo! My new swap works brilliantly on the SSD drive (yup, faster it is!) and is mounted properly, BUT, the root system is still used from the old drive - gparted tells me that the old partition is mounted and the new one isn't. Yes, I can mount and access it manually without problems).

Ok, I tried it without the UUID's. Same result. System boots ok, but mounts the wrong root directory. No matter changing the fstab on both partitions. Yes, BIOS is set to start from the new partition, GRUB is installed (and edited) on the new partition and the changes to it (I use the Grub Customizer GUI, since I don't understand GRUB 2 that well) show up on the splash screen.

So it seems that my system boots on the SSD drive, uses the GRUB configuration stored there, accepts the change in swap drive in fstab, but blatantly refuses to acknowledge the / drive.

_For reference, here's the blkid result:_

/dev/sda5: UUID="ffbe44bc-009c-4f35-b15d-e9eba831f395" TYPE="ext4" 
/dev/sda6: LABEL="sdd-swap" UUID="0592f1f8-bdbc-4133-8fce-de5ac28ddc2d" TYPE="swap" 
/dev/sdb1: UUID="379f921c-8f27-44a6-9982-14318ef64bbd" TYPE="ext4" 
/dev/sdb5: UUID="c4c03399-2baa-486a-baf9-34d8b15d2a57" TYPE="swap" 
/dev/sdb6: UUID="3c9d019f-65f6-41fe-8132-3722d2472d26" TYPE="ext4" 
/dev/sdc1: UUID="e4e9d794-f617-43ad-add6-1e6c0cda3ff7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="6085c940-3552-462a-8181-043fd8d8bc43" TYPE="swap" 
/dev/sdd1: LABEL="KM-CM-$yttM-CM-6jM-CM-$rjestelmM-CM-$" UUID="B2D016FFD016C98D" TYPE="ntfs" 
/dev/sdd2: LABEL="Varasto 2" UUID="8228378128377371" TYPE="ntfs" 
/dev/sde1: UUID="6653-BB29" TYPE="vfat" 

_aaand /etc/fstab:_

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=ffbe44bc-009c-4f35-b15d-e9eba831f395 /               ext4    errors=remount-ro 0       1
/dev/sda5                               /       ext4    defaults        1       1
# /home was on /dev/sda6 during installation
UUID=3c9d019f-65f6-41fe-8132-3722d2472d26 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=0592f1f8-bdbc-4133-8fce-de5ac28ddc2d none            swap    sw              0       0

#define mount point for cdrom drives
#/dev/scd0        /media/cdrom0 auto       ro,noauto,user,exec 0 
#/dev/scd1        /media/cdrom1 auto       ro,noauto,user,exec 0 
#/dev/sr1 /media/cdrom1 iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0

#usbfs for virtualbox
#none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

..

sda5 is the SSD-drive's boot partition (that is not mounted at boot, despite my logic)
sda6 is the SSD-drive's swap (that is somewhat logically mounted at boot)
sdb1 is the old HDD drive's root partition (that is mounted at boot, despite my logic)
sdb6 is /home (that is mounted at boot)


So, please help a guy out here. I'm certainly missing something here and I strongly suspect it to be GRUB, but I'm not quite sure. fstab does partially the things I want, but not wholly. I wouldn't wish to install the linux all over again due to loss of software, but I'm tempted. I also would wish to understand why on earth it doesn't work like I intend (so it's a learning process also - I don't have a computing/engineering degree and don't work in IT - tinkering with linux is more of a hobby of mine).

Thanks!

---

### Post by cebif on 2011-06-23
You could try temporarily disabling sdb1 in the BIOS and seeing if the root partition will boot.

---

### Post by cebif on 2011-06-23
> **Silveri said:**
> 
_For reference, here's the blkid result:_

/dev/sda5: UUID="ffbe44bc-009c-4f35-b15d-e9eba831f395" TYPE="ext4" 
/dev/sda6: LABEL="sdd-swap" UUID="0592f1f8-bdbc-4133-8fce-de5ac28ddc2d" TYPE="swap" 
/dev/sdb1: UUID="379f921c-8f27-44a6-9982-14318ef64bbd" TYPE="ext4" 
/dev/sdb5: UUID="c4c03399-2baa-486a-baf9-34d8b15d2a57" TYPE="swap" 
/dev/sdb6: UUID="3c9d019f-65f6-41fe-8132-3722d2472d26" TYPE="ext4" 
/dev/sdc1: UUID="e4e9d794-f617-43ad-add6-1e6c0cda3ff7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="6085c940-3552-462a-8181-043fd8d8bc43" TYPE="swap" 
/dev/sdd1: LABEL="KM-CM-$yttM-CM-6jM-CM-$rjestelmM-CM-$" UUID="B2D016FFD016C98D" TYPE="ntfs" 
/dev/sdd2: LABEL="Varasto 2" UUID="8228378128377371" TYPE="ntfs" 
/dev/sde1: UUID="6653-BB29" TYPE="vfat" 

_aaand /etc/fstab:_

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=ffbe44bc-009c-4f35-b15d-e9eba831f395 /               ext4    errors=remount-ro 0       1
/dev/sda5                               /       ext4    defaults        1       1
# /home was on /dev/sda6 during installation
UUID=3c9d019f-65f6-41fe-8132-3722d2472d26 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=0592f1f8-bdbc-4133-8fce-de5ac28ddc2d none            swap    sw              0       0

#define mount point for cdrom drives
#/dev/scd0        /media/cdrom0 auto       ro,noauto,user,exec 0 
#/dev/scd1        /media/cdrom1 auto       ro,noauto,user,exec 0 
#/dev/sr1 /media/cdrom1 iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0

#usbfs for virtualbox
#none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

..

sda5 is the SSD-drive's boot partition (that is not mounted at boot, despite my logic)
sda6 is the SSD-drive's swap (that is somewhat logically mounted at boot)
sdb1 is the old HDD drive's root partition (that is mounted at boot, despite my logic)
sdb6 is /home (that is mounted at boot)

In _aaand /etc/fstab:_ you have got the #UUID=ffbe44bc-009c-4f35-b15d-e9eba831f395 it is commented out. I'm not certain but should it be uncommented?

---

### Post by oldfred on 2011-06-24
When you installed grub did you use the new partition and did you update the grub.cfg to use the UUID from the new partition? I think you have updated fstab correctly (did not check details) per your procedure, but grub also has to be correct. 

If you installed grub2's boot loader correctly, you still have to change grub.cfg. It is the one time it is better to edit the file that is not to be edited. You only need to edit one line to boot then run the update-grub.

#Normally we do not directly edit grub.cfg. Edit from liveCD.
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

Once booted
sudo update-grub
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
If not correct drive:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions



If you then boot correctly you can run this to fully update grub.cfg

---

### Post by oldfred on 2011-06-24
If you want all the details on booting:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Silveri on 2011-06-24
A thousand thanks!

After fiddling around a bit with your instructions, I managed to get it to work - at least seemingly. grub.cfg is now reconfigured properly after dpkg-reconfigure.

---

