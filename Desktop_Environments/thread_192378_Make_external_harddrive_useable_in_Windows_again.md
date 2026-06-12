---
title: "Make external harddrive useable in Windows again"
date: 2006-06-08
forum: Desktop Environments
---

### Post by oyvindaa on 2006-06-08
Today I accidently rewrote my external harddrive. It works fine in Ubuntu, but I have to be able to access it from Windows as well, but I can't. When I plug it in and boot up Windows, it doesn't show up anywhere.

Any fix for this?

---

### Post by DarthMandeep on 2006-06-08
If you want to use the drive in both systems, you should format it in the FAT32 format.

---

### Post by oyvindaa on 2006-06-08
[QUOTE=DarthMandeep]If you want to use the drive in both systems, you should format it in the FAT32 format.[/QUOTE]

Yes. Do you know how to do that from within Ubuntu?

---

### Post by aysiu on 2006-06-08
Yes. Plug in the external hard drive and paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install ntfsprogs gparted gksu
gksudo gparted
```

---

### Post by oyvindaa on 2006-06-08
Thanks aysiu.

That was a quality and easy to use program. Worked like a charm.

---

### Post by oyvindaa on 2006-06-08
I've got a few of more questions for you aysiu (or anyone else for that matter.)

1. I have to unplug my usbdisk to be able to boot. Why is this?

2. How do I rename my usbdisk to something more appropriate?

3. After I used gparted and made my usbdisk fat32, I get this:

[img]http://i35.photobucket.com/albums/d163/oaa/desktop.jpg[/img]

The usbdisk is has got 13,5gb free space and the other one's got 37,5gb free space. (The disk is 40gb).
Those two are actually the same disk. I can't remove usbdisk from /media/, because it's only visible when mounted..

Strange one isn't it.

---

### Post by oyvindaa on 2006-06-09
Anyone?

---

### Post by scxtt on 2006-06-09
1. you have to unplug it to reboot - or - you have to have it plugged in inorder to boot @ all?

2. is it defined in your /etc/fstab? -- from what i can see of the USB flashdrive i have, there is some convention that auto-names the drive LEXAR, it's possible that defining it in /etc/fstab will force the use of a different name (that you choose) ...

3. "Those two are actually the same disk." -- this isn't making sense to me, are you saying you have 2 separate 40G disks? - or - that it's showing up 2x's, once as 13G and a 2nd time as 37G?

---

### Post by oyvindaa on 2006-06-09
[QUOTE=scxtt]1. you have to unplug it to reboot - or - you have to have it plugged in inorder to boot @ all?

2. is it defined in your /etc/fstab? -- from what i can see of the USB flashdrive i have, there is some convention that auto-names the drive LEXAR, it's possible that defining it in /etc/fstab will force the use of a different name (that you choose) ...

3. "Those two are actually the same disk." -- this isn't making sense to me, are you saying you have 2 separate 40G disks? - or - that it's showing up 2x's, once as 13G and a 2nd time as 37G?[/QUOTE]

1. I have to unplug it to reboot.

2. No it's not defined in /etc/fstab, I could try that.

3. I know it's not making any sense. I've got one 40gb disk. When I plug it in it looks like two drives get mounted. One 37.5gb and one 13.5gb..

---

### Post by scxtt on 2006-06-10
1. i suppose i can understand that if things are "messed up", the reboot process is getting hung up/confused cause it can't either unmount the drive or even find it ... getting a resolution for #3 might solve problems #1 & #2 ...

2. i tried it 2nite - didn't do much, except when i plugged it in it was /dev/sdd instead of /dev/sdc (the entry i made in fstab) ...

3. is this disk partitioned in any way or was it in the past?

---

### Post by oyvindaa on 2006-06-10
Yes, I used this command "sudo mkfs.vfat -F 32 /dev/sda1" and picked the wrong usbdisk by accident :(

---

### Post by oyvindaa on 2006-07-04
Problem solved with the following command:

```

mkfs.vfat -F 32 /dev/sda

```

This removed the 13.7Gb part of the harddrive.

---

### Post by forrestcupp on 2006-07-20
> **oyvindaa said:**
> Problem solved with the following command:

```

mkfs.vfat -F 32 /dev/sda

```

This removed the 13.7Gb part of the harddrive.

fat32 can't access as large of a partition as NTFS, so if the disk is too big, it will make 2 partitions.  Do you think that is what happened?

---

