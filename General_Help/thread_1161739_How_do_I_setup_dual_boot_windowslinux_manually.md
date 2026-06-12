---
title: "How do I setup dual boot windows/linux manually?"
date: 2009-05-17
forum: General Help
---

### Post by rmjohnson144 on 2009-05-17
I have two hard drives, one with Vista 32-bit and the other with Ubuntu 9.04.  How do I create a dual boot environment without reinstalling anything?

Hopeing for an automated program to do it for me like Ubuntu setup does.  But I'm willing to do some manually editing/programming with a little hand holding.

-=Mark=-

---

### Post by DeMus on 2009-05-17
> **rmjohnson144 said:**
> I have two hard drives, one with Vista 32-bit and the other with Ubuntu 9.04.  How do I create a dual boot environment without reinstalling anything?

Hopeing for an automated program to do it for me like Ubuntu setup does.  But I'm willing to do some manually editing/programming with a little hand holding.

-=Mark=-

When you don't have a dual boot right now, I presume you installed Ubuntu first and then Vista. The Vista installer re-writes the Master Boot Record (MBR) of your first disk and places the start codes for Vista there, neglecting Linux completely as if it does not exist.
The right way is to install Vista first and then Ubuntu. The Grub bootlader will find Ubuntu of course but it will also find the Vista installation and places a line in the boot file. Now when you boot you find choices to start Ubuntu and Vista.

Since this is not working at the moment in your computer we have to do something else.

Start your PC with the Ubuntu live CD, open a terminal (Applications - Accessories - Terminal) and type this (one line at the time):

```
sudo -i
mount /dev/sda# /mnt (mount your linux root partition on /mnt)
grub-install --no-floppy --root-directory=/mnt /dev/sda
reboot
```
This should do it.
Success.

---

### Post by rmjohnson144 on 2009-05-17
> **DeMus said:**
> When you don't have a dual boot right now, I presume you installed Ubuntu first and then Vista. The Vista installer re-writes the Master Boot Record (MBR) of your first disk and places the start codes for Vista there, neglecting Linux completely as if it does not exist.
The right way is to install Vista first and then Ubuntu. The Grub bootlader will find Ubuntu of course but it will also find the Vista installation and places a line in the boot file. Now when you boot you find choices to start Ubuntu and Vista.

Since this is not working at the moment in your computer we have to do something else.

Start your PC with the Ubuntu live CD, open a terminal (Applications - Accessories - Terminal) and type this (one line at the time):

```
sudo -i
mount /dev/sda# /mnt (mount your linux root partition on /mnt)
grub-install --no-floppy --root-directory=/mnt /dev/sda
reboot
```
This should do it.
Success.

OK, just to be clear.  I have Windows installed when I had only one hard drive.  I then added a second hard drive while removing the windows hard drive so as to not ruin it then I installed ubuntu.  I then connected both hard drives and now I have to go into the bios and choose which hard drive boots between windows and ubuntu. 

so, do I make ubuntu the master hard drive when I do this?  will this method still work for my circumstance?

Thanks a lot for your help.
-=Mark=-

---

### Post by Legace on 2009-05-17
Go to Terminal, and type in **blkid** and post output here :) Then we can help you dualboot.

---

### Post by rmjohnson144 on 2009-05-17
well, currently I have Ubuntu as my boot drive and I get this:

```
mark@mark-x58:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ea1cf47a-7b5d-44c2-854a-6222f903aedd" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="dc47207f-0127-4615-a5f8-775b59301683" TYPE="ext3" 
/dev/sdb5: UUID="4256791c-5ba1-4f94-99e6-6aa86f3e21c2" TYPE="swap"
```

I'm guessing I should use my Ubuntu as my boot drive so it doesn't modify my windows drive?  This way If I remove my Ubuntu drive I can still boot into windows?

-=Mark=-

---

### Post by XCan on 2009-05-17
Acutally, the main advantage of using your Ubuntu drive is that if you remove the drive, you will automatically boot into Windows. If it would have been on your Windows drive, the Grub menu would still have appeared upon boot. But it wouldn't have stopped you from booting into Windows anyway. :)

---

