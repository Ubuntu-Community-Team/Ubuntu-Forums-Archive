---
title: "ALERT! /dev/sda1 does not exist"
date: 2009-03-19
forum: General Help
---

### Post by prickly on 2009-03-19
I have come to a dead end with this problem:

I did a P2V conversion of an EeePC with Ubuntu 8.04.1 from here: [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

The conversion was fine but when I boot I get the error: ALERT! /dev/sda1 does not exit - see screens below:

[[IMG]http://img15.imageshack.us/img15/2866/eeepcdevsda1.th.png[/IMG]](http://img15.imageshack.us/my.php?image=eeepcdevsda1.png)
[[IMG]http://img25.imageshack.us/img25/5329/eeepcbootgrub.th.png[/IMG]](http://img25.imageshack.us/my.php?image=eeepcbootgrub.png)

I did find another thread that dealt with this issue and these are the instructions that I followed as a guide (using /dev/sda1 and (hd0,0)): [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

> You have to mount your root partition using the livecd:
Code:

$ 
Code:
sudo mkdir /mnt/root$ 
Code:
sudo mount -t ext3 /dev/sda6 /mnt/rootThen you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$ 
Code:
sudo mount -t proc none /mnt/root/proc$ 
Code:
sudo mount -o bind /dev /mnt/root/devDoing this allows grub to discover your drives. Next you have to chroot:
Code:

$ 
Code:
sudo chroot /mnt/root /bin/bashNow that you're chrooted into your drive as root everything should work.
Code:

# 
Code:
sudo grubI edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.
grub> 
Code:
find /boot/grub/stage1It found mine on (hd0,5)
Code:

grub> 
Code:
root (hd0,5)It successfully scanned the partition and recognized the filesystem-type
Code:

grub> 
Code:
setup (hd0)That was it. It installed and on reboot I was thrown back into Ubuntu.

After this I rebooted and the machine just got stuck at: **grub loading stage1.5**.

I also tried using supergrubdisk to boot the virtual machine without success.

If it is any help the UUID of the virtual hard drive is: 087d4e54-1243-488a-a6f5-e12fbddaf65d.

I have literally been trying to solve this for hours (and have also posted this on the VMWare forums here: [http://communities.vmware.com/message/1203058](http://communities.vmware.com/message/1203058)) without any luck so far, so any help is greatly appreciated!

---

