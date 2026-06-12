---
title: "iPod Touch &amp;/or iPhone"
date: 2008-12-10
forum: General Help
---

### Post by Qloor on 2008-12-10
Please, somebody help me with this problem. I just got my new iPod Touch 2g and so far I have no way of getting past the screen where I'm supposed to connect my iPod to iTunes. I only have one computer and that computer is, of course, Linux. I really need some help unlocking this iPod Touch.

---

### Post by banana jama on 2008-12-10
in rythmbox go to edit--->Plug-ins and make sure the ipod plug in is checked. this maynot work since it doesn't recognize my roomates ipod. if that doesn't work you could try installing itunes through wine.

---

### Post by Qloor on 2008-12-10
> **banana jama said:**
> in rythmbox go to edit--->Plug-ins and make sure the ipod plug in is checked. this maynot work since it doesn't recognize my roomates ipod. if that doesn't work you could try installing itunes through wine.

This has nothing to do with my problem.

---

### Post by randytan on 2008-12-10
Does WINE work with iTunes?

This is one of my major concerns for a dedicated Linux system since I use an iPhone + iPod nano and already have a sizable library in iTunes in the form of music, videos, and pod casts.

Not to mention that in the even that there is an OS update, we need to go through iTunes.

Thanks.

---

### Post by rysh on 2008-12-10
> **Qloor said:**
> This has nothing to do with my problem.

You need iTunes to unlock the iPod ... And iTunes is made for OS X and for Windows ... (thank you Apple :-( ) ... So you need to install windows as i guess you would not buy a iMac or Macbook ...

---

### Post by Qloor on 2008-12-10
> **rysh said:**
> You need iTunes to unlock the iPod ... And iTunes is made for OS X and for Windows ... (thank you Apple :-( ) ... So you need to install windows as i guess you would not buy a iMac or Macbook ...

Right, but do I need to set up a dual boot between the two OSs, or can I just run iTunes in WINE or under VirtualBox with XP.

---

### Post by rysh on 2008-12-10
> **Qloor said:**
> Right, but do I need to set up a dual boot between the two OSs, or can I just run iTunes in WINE or under VirtualBox with XP.

I think you need to make a dual boot system. I had no success with either WINE or with Virtualbox. When you use ext3 as you file system you can install in Windows a driver that you can mount your linux filesystem through the control panel in windows. That way you can drag your movies and music into iTunes ... so it can get copied on the iPod Touch. 

:!:These steps mean that you have to completely re-design your computer setup ... so make backups of important files first.

---

### Post by sigurnjak on 2008-12-11
I use songbird to manage my ipod . Maybe it will work for you and be faster  instead  installing xp just for one task?

---

### Post by rysh on 2008-12-11
> **sigurnjak said:**
> I use songbird to manage my ipod . Maybe it will work for you and be faster  instead  installing xp just for one task?

From their website [http://getsongbird.com/features/](http://getsongbird.com/features/)

i read under Device Support

    *
      Device Support

Songbird's device support is limited. The Device Support wiki has additional details about what's supported. Apple iPhones, iPod Touch and Microsoft Zune devices are not yet supported.

---

### Post by Qloor on 2008-12-11
> **rysh said:**
> I think you need to make a dual boot system. I had no success with either WINE or with Virtualbox. When you use ext3 as you file system you can install in Windows a driver that you can mount your linux filesystem through the control panel in windows. That way you can drag your movies and music into iTunes ... so it can get copied on the iPod Touch. 

:!:These steps mean that you have to completely re-design your computer setup ... so make backups of important files first.

Alright, gotcha. My system won't automatically be overwritten with Windows if I insert the disc for XP, right?

> **sigurnjak said:**
> I use songbird to manage my ipod . Maybe it will work for you and be faster  instead  installing xp just for one task?

I use songbird. Once again, you **must** have iTunes to unlock the iPod.

---

### Post by rysh on 2008-12-11
> **Qloor said:**
> Alright, gotcha. My system won't automatically be overwritten with Windows if I insert the disc for XP, right?

As i said: when you make from a single boot system a dual boot system, you automatically have to think about how big your partition for XP need to be. This space you need to get from the Linux partition ... i don't know what your partition layout is. But i am sure XP will not be friendly for you Linux system ... 

It is possible with some Linux Live CD to use gparted to shrink your Linux partition and get some free space for windows (depends on how much free space you have), but i am not really familiar with this. Windows will overwrite your boot sector! So also for that you need to have some workaround (probably to use a live CD again) to get grub back in the boot sector. IT'S EASY TO MAKE MISTAKES AND LOSE IMPORTANT DATA ... So make a back up of that! DVD's, External HD's or something like that before you begin with XP. 

Good luck!

---

### Post by huanix on 2008-12-13
Dual boot is fine, but the [current] way to go is installing Virtualbox 2.0.6 and running XP as a virtual machine. There are a couple caveats to this, but it's pretty easy:

1. You have to create a mount point in /etc/fstab for usb. If you haven't done this before, you can open a terminal, type "sudo gedit /etc/fstab" and at the very bottom add this line: 

none /proc/bus/usb usbfs devgid=1000,devmode=664 0 0 

(there are better, but more complicated ways to do that.. don't worry if you don't know!)

2. install the non-free version of virtualbox 2.0.6. This is the first version to support the iPhone and only non-free versions support usb. The easy directions are here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)  Don't do the direct download (it won't update), instead, follow the instructions to add the source for virtualbox to your /etc/apt/sources.list so it receives repository upgrades.

3. Now you can install virtualbox-2.0 and (check to be sure that usb is enabled in virtualbox), and install XP. 

Using this method you can even restore or upgrade your iphone: [http://www.huanix.com/2008/11/23/you-can-upgrade-and-restore-apple-iphone-firmware-in-a-virtualbox-machine/](http://www.huanix.com/2008/11/23/you-can-upgrade-and-restore-apple-iphone-firmware-in-a-virtualbox-machine/)

---

