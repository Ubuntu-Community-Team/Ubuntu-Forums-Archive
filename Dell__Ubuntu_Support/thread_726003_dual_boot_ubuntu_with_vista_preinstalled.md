---
title: "dual boot ubuntu with vista preinstalled"
date: 2008-03-16
forum: Dell  Ubuntu Support
---

### Post by stratus17 on 2008-03-16
Hello everybody,

I have a new dell xps 1530 with vista home edition preinstalled.
I would like to dual boot ubuntu on my laptop.
I used Gparted to make some disk space for Linux but I still need to remove one of the 4 Dell parttions.

My question for those who have done it : which partition can I remove that will least influence the existing Vista installation ?
I dont't need Media direct but is it safe to remove that partition ? or the recovery partion ? or the utilities ?
As some of you have certainly done it, I would like to know your experiences. 
Is it easier to reformat the whole disk and reinstall everything without MediaDirect, Recovery and Utilities ?

Second question : is it possible to download a (Dell specific ?) Ubuntu distrib ?

Thanks in advavance for your help.

---

### Post by gbrainin on 2008-03-16
Dell has slightly modified Ubuntu distributions available at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").  However, these are designed with the particular hardware drivers required for the specific computers listed (those that are sold with Ubuntu pre-installed).  Since you're using a different machine, you may be just as well off determining what hardware is in your machine and downloading it yourself.  Before you start, make a comprehensive list of your hardware and check it against the [Hardware Support List]("https://wiki.ubuntu.com/HardwareSupport").

---

### Post by anuban on 2008-03-17
Dual booting Vista Laptop is quite easy as compared to other OS.
You can use the inbuilt functionality in Vista to create space for your new OS - Ubuntu.
Go to 
Disk Management
Select the Vista partition
Right click and select Shrink Volume (I would suggest doing a Disk cleanup beforehand to create more space)
Vista will create space on your Vista partition by shrinking that volume.
That's it...
You got a new partition for your Ubuntu installation.
 
While installing Ubuntu, select the second option on your Gparted screen.  Follow onscreen steps and restart your computer.
 
That's it...:popcorn:
You will have your laptop booting with Ubuntu by default.  You can change that setting by modifying the GRUB.
 
Hope it helps...

---

### Post by enchantedsky on 2008-03-17
After installing Ubuntu, If you want Vista to boot first by default, type in the terminal:

```
 sudo gedit /boot/grub/menu.lst 
```

Enter in your password. This file will allow you to change your boot order. If you need help with that, just search the forums, or reply again :)

---

