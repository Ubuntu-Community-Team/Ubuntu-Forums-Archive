---
title: "Cannot seem to get GRUB Menu"
date: 2020-06-24
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-06-24
Folks,

Main system is Ubuntu 18:04LTS which is dual boot with Windows10 but boots into a GRUB menu.

On an external USB drive I have a number of Linux systems in different partitions including Arch, Debian and RaspberryPi for PC.

After trying to install Ubuntu-mate to a partition on my external drive for some reason the grub menu disappeared and I end up in GRUB RESCUE.

Now I can boot the OSs on the external drive using manual entries in /etc/grub.d/40_custom ---- so once in a system on my external drive I run update-grub, it appears to find all systems but reboot and I end up at grub rescue.  Tried reinstalling GRUB, reports as successful but again end up with grub rescue.  Tried reinstall grub-efi and again end up with grub rescue

lsblk shows the uefi partition mounted correctly.

Whatever I do I end up with grub rescue, not sure why I get this rather than GRUB.

I can boot my systems OK from GRUB on internal drive so no great inconvenience but I am baffled as to why I cannot get a working GRUB menu on my external drive.

Geoff

---

### Post by oldfred on 2020-06-24
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I sometimes chain/configfile from one grub menu to another.
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)
See 6.5 on configfile details
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
Use labels and configfile to boot another install
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359) &
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)

---

### Post by Geoff_Lane on 2020-06-24
> **oldfred said:**
> Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I sometimes chain/configfile from one grub menu to another.
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)
See 6.5 on configfile details
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
Use labels and configfile to boot another install
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359) &
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)

Thank you for very prompt reply but I booted in to Debian in external drive.  lsblk gave active drive as sda so I did sudo grub-install /dev/sda then sudo update-grub /dev/sda

All now working - I've done both those commands numerous times before but did not give the disk location thinking (maybe wrongly) that it would update the correct drive, perhaps it didn't.

Having said that my main internal drive was not altered.

Fortunately, following past advice from you I do have manual entries in /etc/grub.d/40_manual on my internal drive so all was OK.

Thanks,

Geoff

---

### Post by oldfred on 2020-06-24
UEFI or BIOS install?
BIOS version of grub saves drive to reinstall into. If that setting is not correct then grub installs to wrong place.
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 


If UEFI, it installs to ESP that you have mounted in fstab. Full install to any drive other than first drive, typically installs grub to first drive & has that ESP in UEFI. I have to manually change UUID in fstab.

---

### Post by Geoff_Lane on 2020-06-29
> **oldfred said:**
> UEFI or BIOS install?
BIOS version of grub saves drive to reinstall into. If that setting is not correct then grub installs to wrong place.
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 


If UEFI, it installs to ESP that you have mounted in fstab. Full install to any drive other than first drive, typically installs grub to first drive & has that ESP in UEFI. I have to manually change UUID in fstab.

My BIOS is set for UEFI boot.  I have in the past changed to legacy boot to boot an older Ubuntu system I had but the external drive I am referring to, BIOS set to UEFI.

I have checked now, the fstab on my Debian system installed on my external drive is mounting the FAT32 partition that is shown on my external drive.

I've got a small grasp of GRUB, I can boot manually with the basic [B]
set root='hd0,msdos2'
linux /boot/vmlinuz*******  root=/dev/sda1
initrd /boot/initrd.img******
boot

[/B]I know there are other insmod commands that may or may not be important but just using the above four lines I can boot Debian, Arch and RaspberryPi for PC OSs fine.

Not quite sure of the folders within /boot/EFI/efi

Geoff

---

### Post by oldfred on 2020-06-29
I installed Debian to my sdb drive, just to see how grub installed. It installed grub to the ESP on sdb without issue. Where Ubuntu's Ubiquity always installs to sda's ESP, no matter what you select during install. There is a work around in the bug report.

If you want to see where everything is at, run the Boot-Repair report.
I run it, or the part that is/was bootinfoscript to document my system install. Bootinfoscript still works, but does not include NVMe drives, Yann updated the version in Boot-Repair to include NVMe drives.

bootinfoscript - yann's version is in
/usr/share/boot-sav/b-i-s.sh
Now two files also:
/usr/share/boot-sav/b-i-s-functions.sh

Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

baedacool & Peter Maier first part missing p for NVMe drives, but rest ok
[https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript](https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript)
arvidjaar , partitions not pY
[https://github.com/arvidjaar/bootinfoscript/blob/nvme/bootinfoscript](https://github.com/arvidjaar/bootinfoscript/blob/nvme/bootinfoscript)
Old copies:
[https://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/)

---

