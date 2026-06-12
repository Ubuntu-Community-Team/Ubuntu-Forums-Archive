---
title: "Kernel panic on boot of default kernel - system hangs"
date: 2006-08-05
forum: Desktop Environments
---

### Post by burtoni on 2006-08-05
[FONT="Arial"][/FONT]
I am getting a Kernel panic only when booting the default kernel.  When I boot another from GRUB the boot process goes fine.  This also occurred when running Breezy before I upgraded to Dapper.  Specifically the boot log shows the following on default:

[FONT="Courier New"][/FONT]
Booting 'Ubuntu, kernel default'

root(hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz root=/dev/mapper/Ubuntu-root ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x124b1b]
initrd /initrd.gz
  [Linux-initrd @ 0x1fc11000, 0x3decd3 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[4294669.485000] Kernel panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)
[4294669.485000]

[FONT="Arial"][/FONT]
The system then halts and becomes completely unresponsive.  A hard reset will restart the system.  If I choose another kernel the system boots fine and everything runs normal with no problems.  The usual kernel I boot into now is 2.6.15-26-386.  If I boot into recovery mode using the default kernel the system also hangs, I just get more info in the boot log.  The last three lines of this log are:

[FONT="Courier New"][/FONT]
VFS: Mounted root (ext2 filesystem).
VFS: Cannot open root device "mapper/Ubuntu-root" or Unknown-block(0,0)
Please append a correct "root=" boot option.

[FONT="Arial"][/FONT]
My system is home-built with:
ASRock 775VM800 motherboard
north Bridge chipset VIA P4M800 CE 800 MHz FSB
1GB PC3200 RAM
160 GB HDD ATA-133
DVD/CD-RW ATA drive
on-board video S3 Unichrome-pro
On-board audio
On-board ethernet 802.3u

I am hoping that this just requires editing something like a bootrc file.  The initrd file is a compressed file and I'm not sure if that is the one that needs looking at.  Any ideas would be appreciated.

Thanks, Ian.

---

