---
title: "Ubuntu dual boot"
date: 2012-01-28
forum: Desktop Environments
---

### Post by barezi6 on 2012-01-28
Hi everyone
I will install the new ubuntu on my disk1, and later install my windows 7 on disk2, i will have two separate disks, and i want to, when i start my computer appear a menu with my disk1 (ubuntu) and my disk2(windows) and i should what disk i want to go.
I searched on the web and saw many tutorials and tips about dual boot but on the same disk, i am trying to create it some time ago, if anyone can give me some help, it will be great for me

Thanks

---

### Post by oldfred on 2012-01-28
If you install Windows to sdb, it will probably install its boot loader to sda (somewhat like what grub2 does). You want to make sure to install the boot files and the boot loader in the MBR of the same drive as your system install. Some suggest disconnecting one drive and installing. After installing Ubuntu you can run a sudo update-grub after plugging in the Windows drive and it will allow you to boot that.
I might keep Windows as sda which it prefers as it really always thinks it is the only system and have Ubuntu in sdb. You may just have to change which port you plug into the motherboard with if SATA drives.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by barezi6 on 2012-01-28
> **oldfred said:**
> If you install Windows to sdb, it will probably install its boot loader to sda (somewhat like what grub2 does). You want to make sure to install the boot files and the boot loader in the MBR of the same drive as your system install. Some suggest disconnecting one drive and installing. After installing Ubuntu you can run a sudo update-grub after plugging in the Windows drive and it will allow you to boot that.
I might keep Windows as sda which it prefers as it really always thinks it is the only system and have Ubuntu in sdb. You may just have to change which port you plug into the motherboard with if SATA drives.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)


Thank you very much for the help it is great, only one question, i installed the windows 7 and now will install ubuntu, i need to create a windows 7 loader? i am not understading this part of the windows loader

---

### Post by oldfred on 2012-01-28
Did you install Windows to the first drive or the second? We have seen where it put the 100MB (hidden) boot/repair partition on sda when installed to sdb. 

Post this from Ubuntu liveC:, They will in Linux just be NTFS, but the larger NTFS is c: and the 100MB are on same drive you are ok.

sudo fdisk -lu

Windows boot has two hidden parts. The MBR which is what BIOS jumps to to start booting and the PBR partition boot sector which has specific Windows boot code. Grub's boot loader gives you the option to just jump to Windows PBR to boot Windows.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

