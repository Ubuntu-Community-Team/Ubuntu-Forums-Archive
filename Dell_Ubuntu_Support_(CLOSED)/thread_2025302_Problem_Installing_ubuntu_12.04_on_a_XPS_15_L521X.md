---
title: "Problem Installing ubuntu 12.04 on a XPS 15 L521X"
date: 2012-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mm144 on 2012-07-14
I am providing a screenshot as to my problem installing ubuntu.

The L521X has two hard drives, one is the main storage drive and the other one is a msata drive, in my case it's a 128GB msata drive.

When i boot the cd everything is detected, but i cannot install it.

When i hit the install type window, as shown in the screenshot, i have no options at all to install.  The device for bootloader install does not let me select /dev/sda/ or any other drive i stick in usb.

but as the screenshot also shows, gparted, where i made some space for ubuntu on my storage drive, and can access the drive from ubuntu.

I am a little confused.  I did do a search for this computer and all i saw was trying to install ubuntu on the msata drive, which i do not want. Plus i would like to keep the windows partition as well.

---

### Post by mm144 on 2012-07-14
I'd like to add, that i just tried an wubi installation as well and after reboot to complete the install, it complains about the partitions and partition table and hangs.

---

### Post by irv on 2012-07-14
If the  unallocated space is where you want to install you have to allocate it by formatting it to ext4. Do this with gparted and then see if you can see it.

---

### Post by mm144 on 2012-07-14
Thanks for the reply but It Doesn't.  The installer doesn't seem to see the /dev/sda device at all, even though the system itself does.  I say that because the bootloader option on that screen doesn't even allow /dev/sda to be selected and wubi failing when the loopback partition is installed on the windows /dev/sda3.  Although that may be a Coincidence.

---

### Post by iehey on 2012-07-20
Hi,
I have the same computer (l521x) since 2 days ago, and i tried to install ubuntu 12.04 and I have the same issue... (when I have to select a partition, nothing appears, it let me choose only the /dev/sdb, and there isn't any partition visible or usable. If I start ubuntu in live mode and runs gparted i can see all the partitions in my hdd correctly)

After some googling, I tried to disable the SRT from intel to dissable the mSATA cache and use it in AHCI mode, but it doesn't works... after this, I tried to set it in ATA mode, and it doesn't works... (before all, I've parted the hard disk and seting up an ext4 partition, but it doesn't work...)

I will continue searching a solution, if I found something I'll post here...

(Sorry for my poor english level)

---

### Post by Gary Poster on 2012-07-20
I'm considering a purchase and checking out the laptop's Ubuntu compatibility.  I found this thread: [http://ubuntuforums.org/showthread.php?t=2022090](http://ubuntuforums.org/showthread.php?t=2022090)

It looks like it might be what you need.

Gary

---

### Post by iehey on 2012-07-21
Thanks, but in that thread they talk about install ubuntu on mSATA drive...  personaly I prefer to let the mSATA works as a cache drive...

I will try to install it from cd, I heard that it will be a 12.04.1 coming soon, that solves some instalation problems in determinate cases (perhaps this is a usb instalation problem?)

Thanks anyway!

---

### Post by godgough on 2012-07-21
I have a Inspiron 15RSE with 32GB cache and had the same problem.  I managed to get the installer to recognize the disk and installed Ubuntu on my partition but then GRUB does not install.  I have not solved the GRUB problem yet.  I am not sure how the Intel RST handles the MBR(Master Boot Record).

To get Ubuntu to recognize disk I used a few commands in the terminal.  I am no expert and I was not sure exactly what I was doing but here is the link I followed: [https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid]("https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid")

---

### Post by godgough on 2012-07-21
I have found a solution that works for me: [http://ubuntuforums.org/showthread.php?t=2020155]("http://ubuntuforums.org/showthread.php?t=2020155")
The key for me was disabling RST for a restart of the computer.

---

### Post by iehey on 2012-07-24
yeeaah!!

Thanks you so much @godgough!!
it worked for me! I don't needed to use the comands you said in the other thread, the only thing I had to do is:

1. Start Windows, and disable the IRST technology (from intel software inside windows)
2. Reboot the computer, and boot from usb stick (where I placed the ubuntu 12.04 desktop iso with "Universal-USB-installer")
3. Configure the installation and the partitions (like usual, and now it recognized my hdd like normally)
4. And finally, when the process finishes, reboot the computer, start with windows and reactivate the ISRT software, like this, you will have the msata using as usual cache acceleration drive.
5. Reboot the computer, and all is working! (windows and ubuntu)

I hope this helps somebody!

Re-Thanks @godgough

(PD: Sorry for my poor english level)

---

### Post by fermin on 2013-03-19
[COLOR=#000000]iehey or [/COLOR][COLOR=#000000]godgough can you confirm that the laptop runs 100% fine in Ubuntu or are there any issues that do not work correctly? I am considering buying this computer[/COLOR] XPS 15 - L521X BTX and installing Ubuntu on it and need some advice.

---

