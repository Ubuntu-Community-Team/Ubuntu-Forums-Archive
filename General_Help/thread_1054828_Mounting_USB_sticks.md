---
title: "Mounting USB sticks"
date: 2009-01-30
forum: General Help
---

### Post by eholly on 2009-01-30
I am having problems switching USB memory sticks. If I boot with the stick plugged in, it is mounted rw for the user logged in. If I unmount it and re-mount it or mount another stick, it auto mounts read only. How do I mount it rw for a user (not for root only)????


                         E Holly

---

### Post by blazemore on 2009-01-30
You could put a line in the file /etc/fstab to mount it for you.

Run the command
```
fdisk -l
```
Take note of the USB drive's /dev entry: I'm going to assume it's /dev/sdb1.

Now run
```
vol_id /dev/sdb1
```

It will give you the disk's UUID. I'll assume it's a1331d73-d640-4bac-97b4-cf33a375ae5b

Now make a mount point for the usb drive
```
sudo mkdir /usb
```

And now add the relevant line to your fstab:
```
sudo su
echo UUID=a1331d73-d640-4bac-97b4-cf33a375ae5b /usb vfat defaults 0 0 >> /etc/fstab
```

Remember to change the UUID bit, and the mountpoint if you've changed it.

EDIT: Found some more info here: [http://ubuntuforums.org/showthread.php?p=6643778#post6643778](http://ubuntuforums.org/showthread.php?p=6643778#post6643778)

---

### Post by eholly on 2009-01-30
I have modified fstab and still have trouble with a usb stick that wasn't there during boot up. It has a new/different id and auto mounts read only


                         E Holly

---

