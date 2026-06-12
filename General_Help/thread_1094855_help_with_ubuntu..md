---
title: "help with ubuntu."
date: 2009-03-13
forum: General Help
---

### Post by Starn on 2009-03-13
i like to travel. and i have ubuntu installed onto a external harddrive. how could i plug it into a computer via usb and boot via usb?? whould i have to change some thing???
for on my home computer ubuntu installed grub and i can not boot with out my external harddrive plugged in... any help would be great.

---

### Post by circa82 on 2009-03-13
The best way to go about it would be to create a separate /boot partition on your internal hard drive. As it sounds, you're booting directly from the USB which is why you need the external plugged in. If you ran GRUB from the internal HDD, that wouldn't be a factor and you'd still be able to load Ubuntu.

All you really need is 50-100MB of free space on your internal HDD for a new partition. Create that partition using ext2 or ext3 with GParted in Ubuntu (or any partitioner you prefer). There are quite a few steps after that, so it's some work, but a better solution in the end.

If you want to go that route and need help with partitioning, just ask. Otherwise, just be sure the new partition is created on the internal HDD with boot priority.

---

### Post by Starn on 2009-03-13
ok that helps with my home computer... but what if i was to take the external harddrive else where and wanted to boot from their system?
is there away i can do this with out removing ubuntu ???

---

### Post by meierfra. on 2009-03-13
There is not need for a separate boot partition. In fact a separate boot partition would mean that you cannot use the   external drive with other computers. (Edit: the last statement is wrong. See my next post) 

 You just need to install grub to  the MBR of the external drive and install a Windows type MBR to the internal drive:

Open a terminal in ubuntu (Applications->Accessories->Terminal)


Step 1 Install Grub to  the MBR of the external drive.

```
sudo grub
```

and at the "grub>" prompt.

```
find /boot/grub/stage2
```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)

Still at the "grub>" prompt:

```
root (hdX,Y)
setup (hdX)
quit
```

(here X and Y need to be replaced by the numbers you got from "/find /boot/grub/stage2"

Step 2  Install a Windows Style MBR to the internal drive


```
sudo lilo -M /dev/sda mbr
```
Depending on the version of ubuntu you have, you might have to  first install Lilo  via "sudo apt-get install lilo" for this to work.

Also this assumes that your internal drive is /dev/sda. You should double check with "sudo fdisk -lu"


This will solve both you problems. You will be able to boot your internal  drive without the  external drive plugged in. And you will be able to use the external drive on most computers which allow booting from a USB drive.  From version 8.04 on,  Ubuntu has been pretty good in automatically detecting different hardware settings.

---

### Post by circa82 on 2009-03-13
A separate /boot partition on the internal hdd wouldn't keep the OP from booting the external on another computer. It would; however, mean there would no longer be a need for the external to be plugged in during boot. 

Starn: I thought you were talking about a laptop or similar for travel.

As far as whether it would work on 'their' system... that depends on their system. The motherboard would have to support booting from a USB and you would need BIOS to be setup to do so (as in, USB enabled in the BIOSes boot order). Also, the Ubuntu install on your external is setup (I would believe) for whatever computer you installed on. Video, cpu, etc... so if the other computer differs in these areas, tweaking may very well be required. You might find a live CD of Ubuntu to be a better route and simply mount the external when needed (storage and what not).

---

### Post by meierfra. on 2009-03-13
> A separate /boot partition on the internal hdd wouldn't keep the OP from booting the external on another computer. 

You are right. I was thinking about moving the contents of the boot folder to a separate partition. But if one just copies the content, the OP will still able to  boot the external drive for another computer.

Still, as long as the OP's computer supports booting from a USB drive, installing grub onto the mbr of the USB drive and restoring the MBR of the internal drive seems to be the easier solution :)

---

