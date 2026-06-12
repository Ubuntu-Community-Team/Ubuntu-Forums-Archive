---
title: "Grub hdb and iso burning help"
date: 2009-02-22
forum: General Help
---

### Post by LastWho on 2009-02-22
hi,
- regarding this tutorial: [mounting linux partitions in ubuntu ]("http://www.psychocats.net/ubuntu/mountlinux")
how can i make a partition in an hdb get mounted at the boot menu level, while ubuntu is installed on an hda and the pc is booting from this hda? 
(i kept getting "unable to mount selected partition .." or beside the grub menu list, i modified fstab and i believe that i mounted the partition correctly .. check it with gparted which showed me the mountpoint and everything..) i wanted to use this partition as a cd installer [following this guide]("https://help.ubuntu.com/community/Installation/FromLinux"))

- about this tutorial: [downloading and burning an iso of ubuntu]("http://www.psychocats.net/ubuntu/iso")
i downloaded a copy of intrepid desktop via bittorrent, verified it md5 many times with the one in the website, burnt it with brasero, k3b, old and new versions, on cds and dvds, at very low speed (x1 for cd, x4 for dvd) .. and verified each cd/dvd with brasero/k3b, even i made an iso from a dvd with acetone then verified it md5 .. and it was correct .. but when rebooting  i get errors at installation (which won't start) and the check gave me all the times: errors found in 4 files .. :'(
now i m pretty sure that md5 is not accurate and can not guarantee a good copy of ubuntu (8.10 only?)
also i wonder if burning - applications for windows (if my problem was with softwares) (e.g nero) are more effective than the ones on ubuntu???!!!

thank you so much for everything
your website is one my favourite

---

### Post by komputes on 2009-02-24
> **LastWho said:**
> hi,
- regarding this tutorial: [mounting linux partitions in ubuntu ]("http://www.psychocats.net/ubuntu/mountlinux")
how can i make a partition in an hdb get mounted at the boot menu level, while ubuntu is installed on an hda and the pc is booting from this hda? 
(i kept getting "unable to mount selected partition .." or beside the grub menu list, i modified fstab and i believe that i mounted the partition correctly .. check it with gparted which showed me the mountpoint and everything..) i wanted to use this partition as a cd installer [following this guide]("https://help.ubuntu.com/community/Installation/FromLinux"))

The partitions are not mounted, they should be available though the grub console at boot timeif you type in

grub> root (hd

and then you press tab a few times, you will see what partitions are available to you from the boot menu. It should end up looking like (hd0,0) which means first partition on first disk.

If you want to make a CD installer partition on your hard drive, like a recovery partition or guest user OS/"reboot and all the changes are wiped" kind of partition, boot into the LiveCD and Format the drive as a 2.5GB ext3 partition for the iso files and make another ext3 patition and swap for your install. Copy the iso to the 2.5GB recovery partition.

```
$ sudo -s 
# mkdir /media/reinst /media/livecd 
# mount /dev/sda1 /media/reinst 
# mount -o loop /media/disk/ubuntu-8.10-desktop-i386.iso /media/livecd 
# grub-install --root-directory=/media/reinst --no-floppy hd0  
# exit

```
Copy vmlinuz and initrd.gz from /media/livecd/casper/ to  /media/reinst/

Unmount the LiveCD ISO: umount /media/livecd

Copy the LiveCD ISO to the root directory of the partition: cp /media/disk/ubuntu-8.10-desktop-i386.iso /media/reinst/

Edit /media/reinst/boot/grub/menu.lst and add the following:  
```

title=Ubuntu 8.10 Live CD root (hd0,0) kernel /vmlinuz boot=/casper iso-scan/filename=/ubuntu-8.10-desktop-i386.iso spash quiet xforcevesa initrd /initrd.gz

```
Unmount the partition: cd / umount /media/reinst 

Reboot


> 
- about this tutorial: [downloading and burning an iso of ubuntu]("http://www.psychocats.net/ubuntu/iso")
i downloaded a copy of intrepid desktop via bittorrent, verified it md5 many times with the one in the website, burnt it with brasero, k3b, old and new versions, on cds and dvds, at very low speed (x1 for cd, x4 for dvd) .. and verified each cd/dvd with brasero/k3b, even i made an iso from a dvd with acetone then verified it md5 .. and it was correct .. but when rebooting  i get errors at installation (which won't start) and the check gave me all the times: errors found in 4 files .. :'(
now i m pretty sure that md5 is not accurate and can not guarantee a good copy of ubuntu (8.10 only?)
also i wonder if burning - applications for windows (if my problem was with softwares) (e.g nero) are more effective than the ones on ubuntu???!!!

thank you so much for everything
your website is one my favourite

bit torrent packets may get messed with, try downloading it from ubuntu.com

---

### Post by LastWho on 2009-02-26
Thanks komputes for the great tutoriel, un/fortunatly i can't test it because i ve already installed intrepid using the liveCd burned with nero from the same iso i ve donwloaded (via p2p from ubuntu.com)
((its my personal opinion from my personal experience:[INDENT]nero 8.3.2.1 > brasero 0.8.4 or k3b 1.0.4
Md5 file check is not that accurate, like some one may think it is))
[/INDENT]I m dual booting now windows xp and ubuntu 8.10, and** i wonder please, if there is any changes we should apply to your tutorial** if we want to install ubuntu from a small partition on the hdd and make it bootable but without having an OS installed, only:
[INDENT]- an image on the hard disk
- a small bootable linux distribution (like Slax)
- a grub live cd

[/INDENT] (which was my case before installing windows)

i m asking because i followed [this tutorial]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") step by step but couldn't boot from the hard disk!

> 
**Setting up the Destination Drive**

[INDENT]5- Create an exact copy of the iso to the dummy partiton setup in step 2 (Note that this is not the file ubuntu.iso sitting in a formated dummy partition, the iso _is_ the partition. When you get to the last step of this howto, "In the device prompt, provide the device name for the dummy partition, such as /dev/hdaX." you _can't_ enter /dev/hdaX/ubuntu.iso. Can you even acheive this particular dd functionality on a Windows box?)
[/INDENT]dd if=/mnt/usb/ubuntu.iso of=/dev/hdaX 
where /dev/hdaX is the 700MB dummy partition 
[INDENT]6- mount the iso and the root partition and copy two boot files from the iso to the root partition
[/INDENT]cd /mnt
mkdir hda1 iso    [COLOR=Teal]#no need to make hda1, its already mounted [/COLOR]
mount /dev/hda1 hda1  [COLOR=Teal]#no need to[/COLOR]
mount -t iso9660 -o loop /dev/hdaX iso  
cd /mnt/iso/install
cp vmlinuz initrd.gz /mnt/hda1 #[COLOR=Teal]i copied them from /mnt/iso/casper[/COLOR]

where /dev/hda1 is the root partition 
 
**Booting into the Installation**

 
[LIST=1]
[*]Insert the Grub boot disk and reboot / turn on the computer
[*]at the grub boot menu, there are 4 commands you must use to boot: root, kernel, initrd, and boot
[*]use the root command to set the device to boot from, which is in this case, the root partition of your harddrive.  This example uses /dev/hda1, which equates to (hd0,0)
[*]kernel is used to choose the kernel and pass preferences. You can look at the "isolinux/isolinux.cfg" file on the cd or iso to look at boot commands and their "ubuntu boot label" equivalents. This command is typed in on a single line and ends with "--". This example chooses a default ubuntu installation. (Note that this line may wrap on the screen, on a printout, and when typed.)
[*]initrd:
[*]boot: launches into the boot process
[/LIST]
root (hd0,0)
kernel /vmlinuz append vga=normal initrd=/initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
initrd /initrd.gz
boot [COLOR=Teal]#i got errors like: canno't find root, .. even after i changer root=/dev/rd.. to root=/dev/sdbx to the root partition or to the live cd..)[/COLOR]


Thank you so much for your time
have a nice day


(ps: may be later i ll create a small partition and try to make it bootable using ur tutorial and slax live cd, and i ll reporte back)

---

