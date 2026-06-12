---
title: "Dual-ish Booting Question About GRUB"
date: 2013-11-13
forum: Desktop Environments
---

### Post by noahjohn21 on 2013-11-13
Ok, so I want to install Windows 7 (Adobe, I curse you!) on a system I built that is running 13.04, and I have a fear of GRUB.
Now what I want to do is install Windows 7 on *different *hard drive than the one running 13.04, what I want to know is will GRUB understand that there is another drive that is bootable. 
The dive I have now is 1TB in size, and less than a year in is over 60% full ( I'm into photography) so just partitioning the drive will not be good, as I'm moving the whole ecosystem of editing to Windows 7. (I'm sorry, but I need LR5 and After Effects badly) 346 GB of free space will fill up in no time. I'm worried that GRUB will not let me boot into Windows 7 without me having to perform some kind of magic in the terminal, or some kind of data loss or corruption.

---

### Post by oldfred on 2013-11-14
Best to unplug the Ubuntu drive and just install Windows normally. Make sure it it port 0 of SATA ports on motherboard. Then replug in Ubuntu to port1 and set BIOS to boot sdb or Ubuntu drive. After booting run this.
sudo update-grub

That should find the Windows install. And Windows then will not mess with Ubuntu.
Windows installed to a second drive with Linux on first drive that is boot drive in BIOS may get the (hidden) 100MB boot loader installed to the Ubuntu drive. And it will corrupt Linux  as it does not see the Linux partitions correctly.
If not wanting to unplug, be sure to change BIOS to default boot from new Windows drive before installing. Then Windows should install its boot loader to the same drive.

That all assumes BIOS installs, not UEFI. If new system with UEFI post back for totally different instructions.

---

### Post by stinkeye on 2013-11-14
[COLOR="#FF0000"]EDIT[/COLOR] Already answered by oldfred (old[COLOR="#A9A9A9"]fast[/COLOR]fred[COLOR="#A9A9A9"]dy[/COLOR])


If you install Windows7 on another drive, after installation all you need do is set your boot device in the BIOS to the ubuntu drive.
Once logged in to ubuntu, run...
```
sudo update-grub
```
This will pickup the Windows7 install and add to the grub menu.

The boot sector of the Windows7 drive isn't touched and if you encounter a grub problem
you can select the Windows7 drive as the boot device in the BIOS.

For piece of mind you can even disconnect the ubuntu drive while installing Windows7.

---

### Post by noahjohn21 on 2013-11-14
Thank you! That solves my problem.

---

