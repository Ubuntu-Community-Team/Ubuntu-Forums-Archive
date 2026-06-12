---
title: "Avoid auto-mounting of a partition on external usb hard-disk"
date: 2009-05-12
forum: General Help
---

### Post by martin_legion on 2009-05-12
Hello. I wanted some help with this:
I have a removable usb harddisk with two partitions on it.
The first is the vfat partition, accesible in windows when I plug it, and the second is an ext3 partition with linux files.

The thing is that when I plug the disk running Linux, it automatically mounts both partitions. I would like avoid mounting automatically the second partition, the ext3 partition.

I guess I could add a line on fstab with the device refering to the ext3 partition with the noauto flag, but, I would like to make it a little more specific. I don't know if some day I will plug another disk with partitions on it that might have the same name.

I hope I made myself clear...

Thanks!

---

### Post by kpkeerthi on 2009-05-12
> **martin_legion said:**
> I would like to make it a little more specific. I don't know if some day I will plug another disk with partitions on it that might have the same name.


You should use UUID in /etc/fstab instead of device name.
To find the UUID of a partition:
```
sudo blkid
```

See [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab") for examples.

---

### Post by martin_legion on 2009-05-12
> **kpkeerthi said:**
> You should use UUID in /etc/fstab instead of device name.
To find the UUID of a partition:
```
sudo blkid
```

See [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab") for examples.

Thanks for the command, I didn't know how to find out the UUID.
When I get home I'll try that and hope I don't burn anything :P

---

### Post by martin_legion on 2009-05-13
Ok, so I added this line to fstab:
```
UUID=53b796c1-dc91-3be0-747e-30f786d91ad0 /media/somedir ext3 defaults,user,noauto 0 0
```

Then I plug the disk, and... it keeps mounting the partition, only in the path I specified in fstab...

What flags should I use?...

thanksssss

---

### Post by martin_legion on 2009-05-13
> **martin_legion said:**
> Ok, so I added this line to fstab:
```
UUID=53b796c1-dc91-3be0-747e-30f786d91ad0 /media/somedir ext3 defaults,user,noauto 0 0
```

Then I plug the disk, and... it keeps mounting the partition, only in the path I specified in fstab...

What flags should I use?...

thanksssss

AUTO-ANSWER:
It's not a matter of flags. The noauto flag is for avoiding mounting at boot. The solution is enter in gconf-editor, apps-nautilus-preferences and uncheck media_automount (This in Ubuntu Jaunty).

---

