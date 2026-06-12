---
title: "Switching from dual-boot to single-HD?"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Curlydave on 2005-08-17
My Samsung 80GB HD is fried. This was my Windows one. My brother is putting together a new comp and needs a HD. What I was thinking to do to save money is to just buy myself a 120GB SATA 3Gb/s HD and giving him my 40GB Linux HD. I still want to dual-boot, so I could partition my HD into 80 and 40GB partitiona for Windows and Linux like before. 

Now, how difficult is it to do this? How do you set which partition it looks at first so it's the Linux one with GRUB. What do I do to make this transistion? Thanks! (I'm going to have to wipe my Linux setup to do this, but I could back up important things.)

---

### Post by landcross12 on 2005-08-17
You should have no problem with dual boot. Recommend you create the partitions with Windows CD. Next install Windows then install Linux last. (If you install Linux first then Windows will wipe Grub bootloader)

When you add Grub with the Linux install it will include Windows as a boot option,

I have both systems on one hard drive with no problems.  I would suggest creating one small partition formated as Fat partion. This will allow you to share files between both operating systems.

---

### Post by mtelewicz on 2005-08-17
[QUOTE=Curlydave]How do you set which partition it looks at first so it's the Linux one with GRUB.[/QUOTE]

If my understanding of how GRUB works is correct (only somewhat experienced with Linux), then it has nothing to do with your partition.  GRUB, or at least a portion of it, resides on the Master Boot Record (MBR) of your hard drive.  So GRUB will always run so long as that hard drive is scanned for a boot record.  To get GRUB on there, you use grub-install.  Do "man grub-install" for more information.

Everything else is based off of /boot/grub/menu.lst.  I recommend you take a look at that file before you switch your hard drives around.  Here's some snippets from mine.  GRUB is installed on the MBR of my Windows hard drive, in this case, but my default boot is to Linux which is on a seperate hard drive:

#makes entry 0 the default
default         0

#first entry, or entry 0
title           Ubuntu, kernel 2.6.10-5-amd64-generic Default
root            (hd2,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro console=tty0 quiet splash
initrd          /boot/initrd.img
savedefault
boot

#second entry
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

--end--

Another option is to install Windows first, then Ubuntu.  Ubuntu will then setup everything for you automagically.

---

