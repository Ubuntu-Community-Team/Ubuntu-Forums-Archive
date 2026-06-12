---
title: "Installation/partition problem"
date: 2009-01-24
forum: General Help
---

### Post by brandoncolorado on 2009-01-24
Pardon my idiotic question.  I just got a new computer.  I installed Windows 7 first.  I then tried to install Hardy off an old CD twice (it froze both times).  I finally got Ubuntu installed with a new Ibex, but now I have windows, 3 copies of Ubuntu, and 2 random small megabye partitions on my hard drive.  I am including a screenshot of the gparted program.

1)  How do I actually get Gparted to change these partitions?  All options are greyed out.  Is it as simple as restarted with LiveCD?

2)  Which do I delete to keep my current setup?

Thanks

---

### Post by brandoncolorado on 2009-01-24
*image*

---

### Post by Limerick on 2009-01-24
Umm. From what I understand, you can edit the partitions in a program if you select try ubuntu without changing your system when you boot up from the live disk. The program is in the administrator settings type area place. Anyhow, I think the other ubuntus might be extra kernels when I start up it always brings up 27.7, 27.9, their recoveries and this other one I forgot. I tend to ignore em but don't listen to me.

---

### Post by Cosimix on 2009-01-24
THIS IS THE MOST MESSY PARTITION TABLE I HAVE EVER SEEN :)

**Solution** - If you want to get rid of the duplicated copies of Ubuntu do this:

1. Uninstall Windows and never install it again in your life (facultative) 
2. I don't assume any responsability if you mess about with GParted
3. Start Ubuntu from the hard disk and use the **mount** or **df -h**  command to find out which partition is your root ( / ) and home ( /home ). Those are the partitions your Ubuntu is running from. 

Example:
user@laptop:~$ **df -h**
Filesystem               Size     Used   Avail    Use%    Mounted on
/dev/sda6                  4.3G    3.5G    630M     86%      /
/dev/sda7      48G       27G      21G       58%      /home

...You might not have a dedicated partition for home, in this case don't worry about /home.

4. If the partitions that you want to delete have a lower number than / and /home (which seems 2B your case) you have to run a recovery CD/USBstick** in order to delete the partitions. 

5. Reboot the PC with the recovery CD/USBstick and delete the partition using 
[B]sudo cfdisk /dev/sda
[/B]
or fdisk commands

once deleted use the command **partprobe** **/dev/sda** to refresh the kernel's list of partitions so that changes will take effect. Run cfdisk again or **fdisk -l /dev/sda** to double check.
  
Have a look at your new partition table and find out what's the new root ( / ) partition number is.

6. If / and /home partition numbers haven't changed you are done otherwise step 7

7. You are still in the recovery env. Use these commands as root:
user@laptop:~# **grub**
grub> **find /boot/grub/stage1**
 (hdx,y)
grub> **root (hdx,y)**
grub> **quit**
user@laptop:~# **nano /boot/grub/menu.lst**
### Adjust the line in bold to reflect the grub conf, comments in brackets #(comments) ###

title           Ubuntu 8.10, kernel 2.6.27-11-generic

**root            (hdx,y)       **#(as in the grub command)

kernel          /boot/vmlinuz-2.6.27-11-generic **root=/dev/sdaz** ro quiet      #(z = y +1)

initrd          /boot/initrd.img-2.6.27-11-generic


user@laptop:~# **init 6   **to reboot

**Note** if the partitions are mounted you can't delete them. 
** For recovery you can either use Ubuntu Live CD on CD-ROM or USB stick or [R.I.P linux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/") or [Knoppix]("ftp://ftp.uni-kl.de/pub/linux/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso")

YOU OWE ME A PINT !!! :)

---

### Post by brandoncolorado on 2009-01-24
Thank you!

[http://www.pintprice.com/images/homeB.jpg](http://www.pintprice.com/images/homeB.jpg)

---

