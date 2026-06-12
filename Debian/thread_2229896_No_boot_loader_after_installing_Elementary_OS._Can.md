---
title: "No boot loader after installing Elementary OS. Can't boot into any OS."
date: 2014-06-15
forum: Debian
---

### Post by victor36 on 2014-06-15
I'm asking this on the Ubuntu forums because EOS doesn't have forums. I currently can't boot into any OS. The bootloader got hosed somehow.

I have a single 512GB SSD. This is my GRUB Boot-Repair info:

[http://paste2.org/Kdm9Ljsf](http://paste2.org/Kdm9Ljsf)

Windows 7 boot is on sda1
Elementary is on sda5

I don't know grub2 and I'm a beginner to Linux. I can boot into the USB version of EOS. What are the terminal commands I need to run to:

1. Get grub2 to display Windows 7
2. Get grub2 to display Elementary OS
3. Get grub2 to install itself on sda and present these two booting options on system start-up?

4. Note: I tried EasyBCD on Windows before but that only got me into a worthless DOS version of a bootloader. I did NOT remove whatever EasyBCD did because - surprise - I can't boot into anything.
5. I get grub2 to work previously. But I re-installed EOS and now the boot loader is gone.
6. I tried Boot Repair but I keep getting "grub-pc purge cancelled. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]"


[LIST=|INDENT=1]
[*][FONT=inherit]Partition  Boot  Start Sector    End Sector  [COLOR=#408080][FONT=inherit]*# of Sectors  Id System*[/FONT][/COLOR][/FONT]
[*]
[*][FONT=inherit]/dev/sda1    *          2,048       823,295       821,248   7 NTFS / exFAT / HPFS[/FONT]
[*][FONT=inherit]/dev/sda2             823,296   410,943,487   410,120,192   7 NTFS / exFAT / HPFS[/FONT]
[*][FONT=inherit]/dev/sda3         410,943,488   738,623,487   327,680,000   7 NTFS / exFAT / HPFS[/FONT]
[*][FONT=inherit]/dev/sda4         738,625,534   976,771,071   238,145,538   5 Extended[/FONT]
[*][FONT=inherit]/dev/sda5         738,625,536   976,771,071   238,145,536  83 Linux
[/FONT]
[/LIST]

---

### Post by bapoumba on 2014-06-16
*Thread moved to **Other OS/Distro Support**.*

---

### Post by oldfred on 2014-06-16
You have to have working Internet connection for Boot-Repair to run its purge & reinstall as it has to download a new copy of grub2 (grub-pc).

I do not see anything wrong other than it does not look like you have Internet connected. Be sure to use hard wired Ethernet, not wireless.
Grub menu already has Windows in it and looks correct.

The reinstall of Elementary may not have correctly reinstall grub to MBR. So version in MBR is looking for old version. The purge & reinstall would fix it, if that is the problem.

Is this an UltraBook? Or what is sdb 24GB where you have installed swap. If you have 4GB of RAM or more you will probably not use swap. If an Ultrabook see link in my signature. That is on UEFI but the section on Ultrabooks still applies for BIOS. 
If 24GB is a mSATA, I might just install Linux / (root) to that partition, put a small swap of 2GB & /home on hard drive. I would also add a shared NTFS data partition.

---

