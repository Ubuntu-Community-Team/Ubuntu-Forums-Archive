---
title: "Problems with dual booting Netbook Remix OS"
date: 2009-05-27
forum: Desktop Environments
---

### Post by asolo157 on 2009-05-27
All,

Hi, Ubuntu newbie here, so I would really appreciate the help, and please be gentle. I have an MSI Wind U100 Netbook that I was running a Hackintosh version of Mac OS X 10.5.7 on. I booted the laptop with a USB drive of the Ubuntu netbook remix OS on it. I wanted to install the netbook OS, but I also wanted to keep my OS X system on there. 

I used the Ubuntu partition utility to create a new partition for the Ubuntu OS, and then I resized and moved over the Mac OS X partition. I didn't delete or format it though. It was my hope that this process would allow me to dual boot the laptop on startup. However, this has not happened. When I boot the laptop it goes right into Ubuntu with no option to boot to the Mac OS. However, the Mac partition definitely still exists, and all of files are definitely still in it, as I can mount it as a drive in Ubuntu. 

So, what did I do wrong? What do I do to create the option to dual boot into Ubuntu or Mac on startup? Thanks so much for the help.

---

### Post by linesma on 2009-05-27
First off, be advised that using hacked copies of OSX is illeagal.  If you want to run OSX, you should purchase a copy of the OS from Apple, and install it.  There are several tutorials out there for that.

Okay, that being said, in order to dual boot your system, you are going to have to tell GRUB, the Ubuntu bootloader, that there is another operating system on the hardrive.  The process is very simple.  Here are the steps:

1.  Boot your computer to Ubuntu
2.  Open the terminal and type:  **sudo gedit /boot/grub/menu.lst**
    this will open a text editor displaying the file menu.lst.
3.  Scroll to the bottom of the opened file, and add the following:

[B]title Mac OSX 10.5.7 Leopard
root (hd0,1)
savedefault
makeactive
chainloader +1 [/B]

4.  Reboot, and Grub should now realize that another operating system is there and give you a menu to choose which operating system to boot to.

Since you had OSX installed first, you may have to change the second line to read as follows:

**root (hd0,0)**

This method is also used to dual boot Ubuntu and Windows, if you install Ubuntu second.

I hope this helps.

linesma

---

### Post by asolo157 on 2009-05-27
Thanks so much for your help. I actually bought a copy of OS X to make this legal. Your directions worked perfectly. Thanks again.

---

### Post by linesma on 2009-05-27
> **asolo157 said:**
> Thanks so much for your help. I actually bought a copy of OS X to make this legal. Your directions worked perfectly. Thanks again.

Great!  I am glad that you not only bought a copy of OSX but that the directions worked.  I wish you the best of luck.

linesma

---

