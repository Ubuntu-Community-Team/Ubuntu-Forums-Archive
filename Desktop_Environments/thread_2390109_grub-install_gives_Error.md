---
title: "grub-install gives Error"
date: 2018-04-25
forum: Desktop Environments
---

### Post by johnaaronrose on 2018-04-25
My computer is an Intel NUC (bought this year) using UEFI successfully running Ubuntu 16.04. Ubuntu was installed Ok from a USB memory stick created by Startup Disk Creator from Ubuntu 16.04.4 iso image on my wife's Intel NUC Computer (bought a few months ago) running Ubuntu 16.04. 

I installed Ubuntu 16.04.4 (running on my NUC computer booted up from the Ubuntu 16.04.4 installer memory stick) onto a USB SSD, and that USB SSD boots into Ubuntu Ok. However, my Intel NUC computer no longer boots into Ubuntu: it stops at a Grub prompt. A memory stick containing the (bootable) Boot Repair hangs on the splash screen. So I followed some Terminal instructions as follows:
```
sudo fdisk -l -> sda with 3 partitions (i.e. the computer's SSD): same as on my wife's computer:
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BDE0A51E-85A0-45C5-BF15-EF060C53032A


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 452251647 451201024 215.2G Linux filesystem
/dev/sda3  452251648 468860927  16609280   7.9G Linux swap

and sdb with 2 partitions (i.e. the Ubuntu Installer memory stick).
```

```
sudo blkid -> sda with 3 partitions: same as on my wife's computer:
/dev/sda1: UUID="8CF4-7F42" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="002b9f02-646a-4494-9b11-39145634fc11"
/dev/sda2: UUID="f83725aa-582a-4c36-9ad8-738122da2e0c" TYPE="ext4" PARTUUID="ddf0db43-3444-4883-9708-08594435e99f"
/dev/sda3: UUID="3bc5cd50-8486-4b7a-904c-e6d8b9aba53a" TYPE="swap" PARTUUID="d112fc71-360f-41c8-bd44-45f97d3869a6"

```

```
sudo mkdir /mnt/ubuntu
```

```
sudo mount /dev/sda2 /mnt/ubuntu
```

```
sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/sda ->
Warning:...This GPT Partition Label contains no BIOS Boot Partition
Warning:...Can only be installed in this setup by using blocklists...
Error: Will not proceed with blocklists
```

---

### Post by oldfred on 2018-04-25
You are attempting to install the BIOS/CSM/Legacy version of grub2 to a gpt partitioned drive.
That can be done, I did it for years, before I had an UEFI system. But you then have to have a 1 or 2MB unformatted partition with bios_grub flag.

You probably want to reinstall the UEFI version of grub.

Did you then install Ubuntu in BIOS/MBR configuration to flash drive? And install grub to MBR of flash drive during install using Something Else?
You may just need to set UEFI back to UEFI and boot internal drive.
Or if external drive installed in UEFI mode, it replaced /EFI/ubuntu/grub.cfg which is just 3 lines with the UUID & partition info of install. That can easily be edited, once you know how. :)

If you want UEFI repairs, be sure to boot live installer in UEFI boot mode.
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by johnaaronrose on 2018-04-25
I don't understand what's going on. My Intel NUC computer now boots Ok from its own SSD (i.e. none of USB SSD & memory sticks plugged in). One interesting thing is that the black grub menu (of Ubuntu etc) now showed even though I'd previously (using Grub Customizer) got it not to show and to not to wait. I noticed in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)[COLOR=#000000] that NUC is UEFI & EFI:
[/COLOR]john@John:~$ [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"Installed in UEFI mode
john@John:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
EFI boot on HDD
john@John:~$ 

I had previously used ppa Boot Repair but it didn't give me any feedback.

I'm baffled.

---

### Post by oldfred on 2018-04-25
Grub Customizer backs up the grub configuration scripts and adds its own. But a total reinstall of grub probably overwrites the entire  /etc/grub.d folder of scripts.

---

