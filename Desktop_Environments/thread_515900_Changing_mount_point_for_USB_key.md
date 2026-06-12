---
title: "Changing mount point for USB key"
date: 2007-08-02
forum: Desktop Environments
---

### Post by Scorpions4ever on 2007-08-02
Hey all, 
   I recently became an associate member of the FSF and got myself a  [FSF Privacy Key](https://www.fsf.org/associate/support_freedom/fsf-privacy-key.html)

Unfortunately, the software on the key expects the USB key to be mounted on /media/usbdisk. However, when I insert the key on my Ubuntu 7.04 Desktop, the key is automounted to /media/disk and hence the software on it borks (I know, the software really should be fixed, but bear with me here)

To fix it, I have to unmount and remount manually onto /media/usbdisk and then everything works fine. I was wondering if there is a place where I can set it to automatically mount this key onto /media/usbdisk. I would assume it is in /etc/fstab, but I didn't see any entries there to mount to /media/disk. Is there any other place I should look.

By the way, if I have an iPod connected to the system as the same time, the key shows up on /dev/sdc1
```

/dev/sdb2 on /media/MYTOY type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

```
but if I don't have the iPod, it shows up on /dev/sdb1
```

/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

```
which is why I'm not particularly keen on editing /etc/fstab since who knows what it'll show the device as, if I have any other USB device connected.

Any ideas where I should look to mount this device to /media/usbdisk

Thanks in advance.

---

### Post by ugm6hr on 2007-08-02
Do you have access to a Windows installation?  If so - just put the USB in, and select rename (right-click) in My Computer.  Call it **usbdisk**.

That will then automatically mount at /media/usbdisk whenever inserted into Ubuntu.

If you don't have access to Windows - it can be done from within Ubuntu (but I haven't):
[http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label](http://doc.gwos.org/index.php/Understanding_fstab#How_to_Label)
Look at the FAT section.

---

### Post by Scorpions4ever on 2007-08-02
Thanks for that. I tried using the Ubuntu method and the Windows method and they both worked as far as changing the label name goes. Unfortunately, for a FAT system, the volume label is always set as uppercase, even if you specify the volume label as lowercase.  This happens whether you set the volume label via mlabel or Windows explorer. Hence, the key mounts as /media/USBDISK instead of /media/usbdisk and therefore the program on the key doesn't work.

Do you have any other suggestions?

---

### Post by wkulecz on 2007-08-03
Have you tried a symbolic link (ln -s) from USBDISK to usbdisk in /media?

As root: (sudo -i in a terminal gets you a root prompt)

  cd /media
  ln -s USBDISK usbdisk

worth a try.

---

### Post by sabrewolf2006 on 2007-08-03
You could add a rule to udev to make sure its mounted the same way..

[http://www.wlug.org.nz/UDev](http://www.wlug.org.nz/UDev) - I think this explains pretty much what your after..

Hope this helps

---

### Post by leong on 2007-08-04
open the usb drive icon at desktop properties , volume > setting > mount point , type in the name you need. 

and remount it , it well be active ; every time you plug in will as a same name .

---

### Post by thesonisshining on 2007-08-04
> **leong said:**
> open the usb drive icon at desktop properties , volume > setting > mount point , type in the name you need. 

and remount it , it well be active ; every time you plug in will as a same name .

Okay. I just did this and now my drive won't mount. how do i fix this?

---

### Post by leong on 2007-08-04
are you use the "/" mark ? just the name no dir; disk mount will make the dir under /media went you plug in .(for temp)

try manually mount it and change the mount point , the other **two** option just let in blank , disk mount will do it for you , 

sorry for inconvenient !

---

