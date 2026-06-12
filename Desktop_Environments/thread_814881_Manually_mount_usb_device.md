---
title: "Manually mount usb device"
date: 2008-06-01
forum: Desktop Environments
---

### Post by yedidel on 2008-06-01
Hello,

When I plug in my flash disk, ubuntu mounts it automatically. The problem is, if I unmount it, I have no way of re-mounting it manually without taking it out and inserting again. This is a problem with VirtualBox since when I mount the disk on the guest it unmount on the host, and then i cannot remount it.

Any suggestions?

---

### Post by bingoUV on 2008-06-01
In Places -> Computer, can't you right click on the flash disk in the left panel and select mount?

---

### Post by yedidel on 2008-06-01
it doesn't appear there after i unmount it from virtualbox

---

### Post by rajaram_s on 2008-06-01
often there is also this problem that I find with USB devices. It says the drive is read only... Even if I remove it and plug it again, it gets mounted as read only only.... Then I will have to plug it in windows and then get it back to linux to make it read and write.... why this problem? any solutions?

---

### Post by anv on 2008-06-01
I noticed this same thing after installing 8.04, in earlier I have been able to mount unmount those usb tools. now it is just automount when plugged in and then eject. it is uncomfortable because I have 3 partitions on my usb disk and it is not possible to unmount one of them. If I push eject option from menu it just automounts them again.

---

### Post by buntu_Geek on 2008-06-02
You can use the mount command... its very simple...

For this you have to know the usb device label.... its normally sdb1 sdbx in general...

```

sudo mount /dev/sdb1 /media/disk

```

REMEMBER: You have to create the folder /media/disk before mounting....
```

sudo mkdir /media/disk

```

---

### Post by p_quarles on 2008-06-02
I find 'pmount' easier, since it is designed to be closer to the kind of hotplugging that HAL is designed to take care of automatically. 

```
pmount /dev/sdb1 /media/sdb1
```
Note the lack of "sudo" -- pmount usually does not root privileges, depending on the kind of media being mounted. Also, it is able to create a temporary mount directory in /media based on the input you give it, so there is no need to create one beforehand.

---

### Post by rajaram_s on 2008-06-02
and how do I find the device label?
sorry am not used to mount commands since I never had to know them... I started using ubuntu only from gutsy, which always has auto mount..

---

### Post by buntu_Geek on 2008-06-02
I dunno know any commands as of yet... (probably one reading this might enrich me witht that knowledge.. :D )

I just open gparted (System--> Admin-->Partition Editor)

And see the devices there... on the top you have a drop down list of devices... when you select an appropriate device.... you will have the list of partitions in that devices with their device labels.... and even their mount points (if they are mounted..)...
If you dont have gparted.. you can install it using aptitude...(or the Add or Remove Apps.. search for partition editor...)

---

### Post by p_quarles on 2008-06-02
> **rajaram_s said:**
> and how do I find the device label?
sorry am not used to mount commands since I never had to know them... I started using ubuntu only from gutsy, which always has auto mount..
The simplest way is to type:
```
sudo fdisk -l
```
That lists all attached devices, along with the logical names.

This is essentially the same as what buntu_Geek suggested -- fdisk is, like Gparted, a partition editor. The advantage is that fdisk is lighter, and works from the command line.

---

