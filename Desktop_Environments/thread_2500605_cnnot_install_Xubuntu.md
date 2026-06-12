---
title: "cnnot install Xubuntu"
date: 2024-09-06
forum: Desktop Environments
---

### Post by Autodave on 2024-09-06
Win11 on nvme.  Mint on partition of 4TB spinner.  Mint got messed up when I tried ti align the 2 monitors with one above the other (ongoing issue with RTX3080 where a phantom monitor #1 exists).  This had previously worked with no issue, but today it had issues: only had blank screen on both monitors.  ing that I tried would work.  Decided to back to xubuntu 24.04.  Booted machine with install medium.  Chose to erase disk and install 24.04.  Everything appeared to be going normally, but upon rebooting after install, all I have is 2 monitors both displaying "xubuntu" in the middle of their screens.  I have tried this 3 times now with the same result.  Any suggestions?

---

### Post by Autodave on 2024-09-06
Update:  I can now access Xubuntu by using the boot menu and choosing Xubuntu.  So, GRUB is obviously screwed up.  Additionally, I cannot access the rest of the 4tb spinner drive.

---

### Post by Autodave on 2024-09-06
My 4tb spinner drive which has Xubuntu installed on a 1tb partition, is still not readable for the other 3tb section.  It does not appear in gparted either.  Any idea?

---

### Post by Autodave on 2024-09-06
gparted showing a 3.64tb ext4 at /dev/sda2

---

### Post by yancek on 2024-09-06
Boot Xubuntu and run either of the commands below and post the output.  If you use fdisk, remove all the loop entries before posting.

```
sudo parted -l
sudo fdisk -l
```

What Grub version are you using?  From a terminal run:  grub-install --version

---

### Post by Autodave on 2024-09-06
(GRUB) 2.12-1ubuntu7

Model: ATA WDC WD40EZAZ-22S (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1128MB  1127MB  fat32              boot, esp
 2      1128MB  4001GB  4000GB  ext4


Model: PNY CS1030 500GB SSD (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  17.8MB  16.8MB               Microsoft reserved partition  msftres
 2      17.8MB  542MB   524MB   fat32        EFI system partition          boot, esp
 3      542MB   490GB   490GB   ntfs         Basic data partition          msftdata
 4      490GB   500GB   10.1GB  ntfs         Microsoft recovery partition  diag

---

### Post by Autodave on 2024-09-06
What I really need right now is to get use of 3tb of the 4tb drive.  Xubuntu is (or should be) running on a 1tb partition.  The remaning 3tb needs to be formatted to NTFS so that it can be used for storage of files for both Linux and Win11.

Also, getting GRUB fixed would be a plus.

Thanks for the reply!

---

### Post by Autodave on 2024-09-06
OK....tried the grub repair to no avail.  I can boot into Win11 or Xubuntu 24.04 by going into the boot manager.  My Xubuntu install right now is very minimal.  At this point, I would like to delete grub and Xubuntu.  Then, I would like to format the 4tb drive and reinstall Xubuntu 24.04 onto that drive without reinstalling grub.  Is that possible?

---

### Post by yancek on 2024-09-07
> What I really need right now is to get use of 3tb of the 4tb drive.  Xubuntu is (or should be) running on a 1tb partition 

That is not what your parted output shows.  It shows an EFI partition at the beginning of the drive with a size of 1127MB and a second ext4 partition taking up the rest of the drive which is apparently where your Xubuntu is installed as shown below.

>  2      1128MB  4001GB  4000GB  ext4

You can boot the Xubuntu install media and use gparted or similar software to shrink that partition and allow free space on which to create a data partition.  You can't resize a partition which is in use so you would not be able to do this from the installed Xubuntu.

---

### Post by Autodave on 2024-09-07
Update: got the 4tb drive straightened out now.....Thank you!  Now, if I could get GRUB straightened out, that would be great.  At the moment, I can boot into either Win11 or Xubuntu by using the boot menu.  But it would really be nice to have GRUB functioning again.

---

### Post by yancek on 2024-09-07
What boot menu?  Are you referring to the BIOS firmware Boot Options?  Are you selecting the windows drive to boot windows, the ubuntu drive to boot ubuntu?  When you look at the /boot/grub/grub.cfg file on Xubuntu, do you see a chainloader entry for windows?  If so, post it here.  If you don't have it, have you run sudo update-grub from Xubuntu since you got both systems running?  If not, try it and watch the output to see if a windows entry shows.

---

### Post by ajgreeny on 2024-09-07
OK, you have run boot-repair and it got you nowhere, but you have not shown us the boot-info script output which we may find much more useful than your uncertsin descriptions of what you have on disk and what you have tried so far.

So, see Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.	

**Do not run the default repair or any other repair just yet** but simply copy back here the pastebin link you get which will show us a lot more detain about your system.

---

### Post by Autodave on 2024-09-07
Pastebin:    [https://paste.ubuntu.com/p/nrcz8V7MWx/](https://paste.ubuntu.com/p/nrcz8V7MWx/)

---

### Post by Autodave on 2024-09-10
bump

---

### Post by yancek on 2024-09-10
I asked 2 days ago if you had a windows chainloader entry in your /boot/grub/grub.cfg file and whether you had run sudo update-grub and you have not answered??

In your boot repair output, beginning at line 13 the contents of the nvme drive EFI partition shows both windows and linux EFI files inclding grub.cfg.  This is where windows is installed, partition 3.  Beginning at line 43, the contents of the sda drive EFI partition which shows only linux EFI files including grub.cfg, xubuntu on sda3

Beginning at line 88, the efibootmgr output shows 2 ubuntu entries but you have only one installed:  Boot0003 ubuntu, Boot0005 ubuntu

Boot repair shows the below, that you are booting currently from Boot0003 so Boot0005 is an old, useless entry.
BootCurrent: 0003

On line 205, you see the contents of the grub.cfg file on the windows drive which is pointing to a UUID which does not exist which you can see by looking at the output of blkid beginning at line 175.

At line 211 of boot repair you see the contents of the grub.cfg file on sda1 which is the EFI partition on the ubuntu drive and point to sda2 with the correct UUID for that partition so that is what you are and should be using.

Have you tried running sudo update-grub while booted to the newly installed Xubuntu with both drives attached?  Did you see any output for a windows entry?  If you look at the grub.cfg file on the Xubuntu partition and see a chainloader entry for windows, check the UUID and see if it is:  DD55-79EC  If that is the entry, it is incorrect as the windows EFI files are on the partition with the UUID of:  7E94-CA99

If you want, you can open the /boot/grub/grub.cfg file on the system partition of your Xubuntu install as root (use sudo) and copy and paste the entry below there,save the file and reboot to see if you have that entry showing on boot and windows boots.  If it does, make the change permanent by adding the entry to the /etc/grub.d/40_custom file.  If this does not boot windows, report in detail exactly what you did and the results.

---

### Post by Autodave on 2024-09-10
Yancek: I thank you for your time and energy put into that reply and your previous one.  I really do!  But, I get a headache just trying to understand what I need to do.  Maybe it is because I am 70 years old....dunno.

I did get into the BIOS and managed to get the machine to boot directly into Xubuntu, so since Xubuntu is my primary OS, I guess that at least for now, I will live with having to get into Win11 by going into the boot menu and picking it there.

Again, I greatly appreciate the time and effort that you put into your replies!  Maybe some day in the future I will try to do what you suggested and report back.  But again, I just think that it is, right now, not worth the effort and headache.

Thank you!!

---

### Post by tea for one on 2024-09-11
As you can boot into both systems via the PC boot menu, it would be a worthwhile to follow yancek's suggestion in post 15.
Boot into Xubuntu, open a terminal:-
```
sudo update-grub
```
Did Grub find the Windows Boot Manager?
Either everything stays the same or "GRUB straightened out" will transpire.

---

### Post by yancek on 2024-09-11
Most of the information in my post 15 is an explanation of why you should run sudo update-grub, you don't need to understand it.  Try it and you will see one of the results indicated in post 17.  You should be able to access the /boot/grub/grub.cfg file and look through  for a windows entry and if you have one, make sure the UUID is correct.  I meant to post an entry in my earlier post but forgot it so the entry below should work as explained in my earlier post.  You have 2 EFI partitions and it may have the wrong one but this is just a guess as we don't know the contents of the grub.cfg file.

>  menuentry 'Windows Boot Manager '  {
    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root 7E94-CA99
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

> Maybe it is because I am 70 years old 

Ah,... to be 70 again.

---

