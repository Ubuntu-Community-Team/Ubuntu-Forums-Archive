---
title: "Cannot install windows in a ntfs partition"
date: 2009-03-07
forum: General Help
---

### Post by tejasvn007 on 2009-03-07
Currently i have only ubuntu 8.10 on my laptop.
I want to also install Windows on a separate drive. I formatted this drive to ntfs using gparted.
Now when i try to install windows, the windows setup cd doesnt recognize the ntfs partition and hence could not install windows.

How do i install windows on my laptop?

---

### Post by beno1990 on 2009-03-08
When you created the partition table on the drive you plan to install Windows on, did you make sure you created an msdos partition table? That's the only type Windows can use.

In fact, if you're installing it on a completely seperate drive, it might be better to wipe the drive clean and let the XP installer partition it itself.

---

### Post by tejasvn007 on 2009-03-08
I am sorry, by saying separate drive i meant separate partition on same hard drive.
And i created the ntfs partition using gparted in ubuntu.
Now how do i proceed?

---

### Post by beno1990 on 2009-03-08
Delete the NTFS partition you created in gparted and during the Windows installation, tell it to use the unpartitioned space.

---

### Post by tejasvn007 on 2009-03-08
I deleted the ntfs partition. 
The windows xp setup disc doesnt even recognize the hard drive.
Windows vista setup disc cannot use the unpartitioned space to install even when i create the new partition during setup.

---

### Post by sanus|art on 2009-03-08
Install it in VirtualBox.

---

### Post by jocheem67 on 2009-03-08
If xp doesn't recognize your harddrive at all, then this certainly is a windows-problem;)

Firstly check your bios, is your drive recognized there and set up?

Secondly you can try from within ubuntu to delete the ntfs partition, and idd let vista/xp manage your windows setup...
Did you create a primary partition using gparted? That's what windows needs...

Thirdly, if you're new to partitioning, I would recommend to install windows first, on the beginning of the harddrive..I would create a ntfs partition of let's say 20 gigabytes and leave the rest blank...
After the win install one can safely use the rest for ubuntu...

2 advantages:
The grub bootloader will put xp/vista in automatically, and windows likes it better on the beginning of the disk ( as said )..
Then if you decide to get rid of ubuntu, you won't have probs booting xp/vista
Lastly, I would put grub on the ubuntu partition..and make that partition bootable, that way windows won't be affected.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This explains a lot.

---

### Post by mike555 on 2009-03-08
You might need to clear the MBR , if the hard drive had Ubuntu on it..... 

In Linux , (or live cd) in terminal type;

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1



That will erase any MBR. If your drive is not /dev/hda then please use
the proper one (such as /dev/hde or /dev/sda or what have you)
Please remember also, that Windows REQUIRES the use of the first Primary
partition and it *WILL* assume it is the ONLY operating system to be on
the machine. This WILL cause you difficulty.

---

### Post by ramaCatur on 2009-08-16
> **mike555 said:**
> You might need to clear the MBR , if the hard drive had Ubuntu on it..... 

In Linux , (or live cd) in terminal type;

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1



That will erase any MBR. If your drive is not /dev/hda then please use
the proper one (such as /dev/hde or /dev/sda or what have you)
Please remember also, that Windows REQUIRES the use of the first Primary
partition and it *WILL* assume it is the ONLY operating system to be on
the machine. This WILL cause you difficulty.


Hello, I have same problem. I foloow your solution but after I write 
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 , my hardisk is formatted.
Can I recovery my data. Or the data is not formatted???

If data is not formatted, what can I do after I follow your solution???

Thanks before...

---

