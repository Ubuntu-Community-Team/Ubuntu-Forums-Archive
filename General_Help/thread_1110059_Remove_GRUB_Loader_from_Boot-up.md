---
title: "Remove GRUB Loader from Boot-up?"
date: 2009-03-29
forum: General Help
---

### Post by chrini on 2009-03-29
Hello,

I've done some searching on removing the GRUB loader, but I have a special case and I want to double check with the experts before proceeding.

In my "special" case I am using an Ubuntu 8.04 install on a USB Pen Drive and a Windows XP Pro install on my main HDD. The problem is that I _HAVE TO_ have the USB drive inserted in order for any OS to boot (other wise I get a GRUB Loader error). But what I want is for Windows to boot every time EXCEPT when I have the USB drive inserted (and "boot from USB" selected). 

When I was testing the installation of Ubuntu 7.04 on my USB drive, it worked fine (booting to windows except when the usb drive was inserted). But now that I have installed 8.04 it isn't working... I think it may have been something I overlooked during the install process.

At any rate, are there any suggestions? Can I simply run "fixmbr" in recovery mode of the Ubuntu Install CD? (or am I misunderstanding the instructions).

Any help is appreciated. Thanks!

-Nick

---

### Post by nebileix on 2009-03-29
Are u trying to say that u wanna boot from the usb drive when it is inserted during post? If your bios support that, I dun see the problem.

As for the grub error, currently the loader couldn't find the boot file. So if you wan Windows boot loader to be default, insert your Window cd and run recovery console and do the 'fixboot' or 'fixmbr' Cant really remember the command. But theres alot of guide avaliable.

---

### Post by constantinos692 on 2009-03-29
I had the same problem. I wanted to remove GRUB because there I had an error. The way that I found was through the HIREN'S boot cd. Have a look at the internet and you will find it. At the MBR menu you will find the tools that you need. Unfortunately I can't give you more information because it was same time ago and I don't remember but if you have a look you will find. what you need is to determine the Windows partition/hard disk as the master boot, the place where your computer will search for the operation system. When you manage to do that when you reboot you will boot just like there is no other operation system than Windows in your computer. But remember if there is an other operation system you will loose it. You will have to install it from the begining.

---

### Post by meierfra. on 2009-03-29
To fix your problem, you need to install grub to the MBR of the external drive and and repair the MBR of the internal drive.
Open a terminal in Ubuntu (Applications->Accessories->Terminal

** Step 1 Install Grub to the MBR of the external drive.**

```

sudo grub

```

and at the "grub>" prompt.

```

 find /boot/grub/stage2

```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2' )

Still at the "grub>" prompt:




```

root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")


** Step 2) Install a Windows Style MBR to the internal drive: **


```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

(Here "/dev/sda" needs to be the device name of your internal drive. It
probably is "/dev/sda" but you should double check via "sudo fdisk -lu")


Step 3 Edit Menu.lst so that you can boot to Windows from the Grub menu.

Open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Look for the item which looks something like

title XP
root (hd0,?)
savedefault
chainloader +1

Replace the line

root (hd0,?)


by the the three lines

root (hd1,?)
map (hd0) (hd1)
map (hd1) (hd0)

Save the file.

If you boot from the internal , you should boot directly into XP. If
you boot from the external drive, you should get the Grub menu, which lets
you boot into XP and Ubuntu

---

