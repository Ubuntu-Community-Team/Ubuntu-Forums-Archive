---
title: "Help: I want to dual boot Windows XP from a slave drive"
date: 2006-09-18
forum: Desktop Environments
---

### Post by lybertyboy on 2006-09-18
I sure hope someone can help me on this problem.  Don't ask me why, but I'm trying to dual boot into XP from Grub off of a slave drive.  I've done fdisk from the terminal and this is what I get:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4865    39078081   83  Linux
/dev/hdc2            4866        4982      939802+   5  Extended
/dev/hdc5            4866        4982      939771   82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2433    19543041    7  HPFS/NTFS

When editing grub, what do I need to put in so that I can boot into XP?  I know that Windows doesn't like booting from a slave drive, but I know there are some work arounds.  I just haven't been successful at implementing them as of yet.  If anyone can help me on this, I would apprecate it very much.

---

### Post by lagagnon on 2006-09-19
Read this:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Booting_Windows_on_second_HD_with_Grub](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Booting_Windows_on_second_HD_with_Grub)

that took me 5 seconds to find by typing the following keywords into Google: Windows slave drive boot grub. Easy eh?

---

### Post by lybertyboy on 2006-09-19
Yeah, thanks for your "help."  I've already tried that, unsuccessfuly.  GRUB doesn't boot into windows.  It just sits there.  I thought the Ubuntu forums would be different, but I see that they are filled with the same 30 year old male with a 6 year old wit as every other forum.

---

### Post by crispy_420 on 2006-09-19
If I remember correctly, been a bit since I did a dual boot, windows wants to reside on the master drive. That was even the case of dual booting two versions of windows (WinXP & Win2000). 

You have one of two options depending on your goals. But this is just my opinion.

**_PLAN A:_**

Dual boot with windows on master and then Ubuntu either on the same drive on a different partition or on the slave drive. But you will need to install windows first then linux.

Plus: free
Cons: starting over

**_PLAN B_**

Install windows or ubuntu on a swappable drive. That way you can remove one and put the other in when needed. I do this for mainly testing various new OSes that I snag from distrowatch. They are officially know as removable racks. You buy one initial setup and the buy buy as many trays as needed.

Plus: no screwing up both OSes and no starting over
Cons: it will cost you, but not too much. around $30-40 (US).

---

### Post by lybertyboy on 2006-09-19
Thanks.  I appreciate some real help.  I happen to have some racks already.  I think I'll give it a try.

---

### Post by BoneKracker on 2006-09-19
IF you want to be able to actually dual-boot AND you need to keep one of your existing OS installs intact, you might want to consider the following:

1.  Switch windows drive to master and ubuntu drive to slave.
(Depending on your machine and your preferences, choose whether to do this in your BIOS, or by using drive jumpers, or by physically swapping drives and verifying your BIOS and jumpter settings are correct).

2.  Insert the Windows install CD and either: 
(a) reinstall Windows if it's a brand new install; 
(b) use the recovery console utilities if you are experienced with them to fix the mbr and boot scripts; or
(c) re-run the Windows installer, but select "Repair".  

3.  Verify that Windows boots when you restart the computer (it should have set up the new master drive's MBR to point to the NTLoader and your system should basically be ignorant of Ubuntu's presence at this point).  Get Windows booting before proceeding.

4.  Boot from Ubuntu install CD and either:
(a) reinstall Ubuntu if your Ubuntu install was new (this should automatically set up GRUB properly); or 
(b) do a reinstall of GRUB (all of these steps may not be required - you'll probably get some additional advice about this part from somebody smarter than me)
     i.  create a mount point for your ubuntu installation
```
sudo mkdir /mnt/ubuntu
```
     ii. mount your ubuntu directory there
```
sudo mount -t ext3 /dev/hdd1 /mnt/ubuntu
```
     iii. prepare to chroot
```
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo mount -t proc none /mnt/ubuntu/proc
```
     iv. chroot
```
sudo chroot /mnt/ubuntu /bin/bash
```
     v.  reinstall grub
```
sudo rm /boot/grub/menu.lst   #not sure this is necessary, but just in case
sudo apt-get update
sudo apt-get install grub
```
     vi.  make sure grub's instatiated on the right drive (not sure needed)
```
sudo grub
> root (hd0,0)    # I don't know whether it's hd0 for you or not
> setup hd0       # Ditto
> quit
```
     vii.  make sure grub menu is right.
```
sudo nano /boot/grub/menu.lst
```
#look it over and fix it if it's wrong.  Next line only if you changed it
```
sudo update-grub
```

5. Reboot and test your grub menu and fix any problems (you can test changes to the grub bootlines by using the 'e' option while grub menu is running, then make them permanent later by editing menu.lst).

---

