---
title: "udev Permissions for digital camera mount point"
date: 2009-03-26
forum: General Help
---

### Post by salukibob on 2009-03-26
Hi There,

I'm writing a web-app (PHP) that I'd like to be able to read images from a digital camera. At the moment, you just pass it a directory path, and it creates thumbnails from the images found.

However, once my camera is plugged in, my app cannot open the directory to gain a listing of whats on it. The mount point is /media/LUMIX, and is mounted using my username (rob) and the root group. This is the output from mount: 

*/dev/sdb1 on /media/LUMIX type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)*

My web-app runs under apache2, with the username and group of www-data. I've added the user www-data to the plugdev group, but thats been no help. I also took a look at my /etc/udev/rules.d/40-permissions.rules file, and found this line:

*SUBSYSTEMS=="usb", GROUP="plugdev"*

I added a mode to this, as so:

*SUBSYSTEMS=="usb", GROUP="plugdev", MODE="0666"*

and restarted udev, but again no joy. 

So my question is, how can I give the www-data user permission to access the /media/LUMIX mount point? I really only want read permission, but i'd be interested to know about write permissions as well to allow for image deletion if I go that way.

Just to make things a bit trickier, I would like this to work with any digital camera, and preferably any type of usb removable storage media. 

Thanks for any advice,
Rob

---

### Post by salukibob on 2009-03-26
I've just been reading a little about libgphoto2 and about HAL. Am I looking in the wrong place with udev? Should I be looking at HAL rules?

I find the multiple solutions to usb hot-plugging quite confusing!

Thanks
Rob

---

### Post by salukibob on 2009-03-26
Ok, so after a lot of digging i've found out that the camera is mounted using HAL. The filesystem is FAT32, and so doesn't have any permission information. Therefore HAL uses the default of read/write/execute for user only. I'd like to change this, but have no idea where to look. 

Preferably i'd like to change it only for digital camera devices.

Please can anyone help?

Thanks
Rob

---

### Post by unutbu on 2009-03-26
Open a terminal and type
```

getent group www-data
```

You should see something like 
```
www-data:x:33:

```

Above is a colon (:) separated list. Note the number in the third column. In the above example, it is 33. This is the GID (group ID number) of www-data. Yours probably says 33 too; the above command is just to make sure.

Now plug the USB removable storage media into a machine running Ubuntu desktop.
For each partition on the USB drive an icon should appear on the desktop.
Right-click on the icon associated with /media/LUMIX
Select Properties
Go to the Volume tab
Click on the Settings>Mount options. Add
```

gid=33,dmask=007,fmask=117
```

On the off-chance that www-data's GID is something other than 33 on your system, change "gid=33" appropriately.

Since your /dev/sdb1 (/media/LUMIX) partition is a vfat partition, the owner, group and permissions are set for the entire filesystem at mount time. The above options sets the group to 33 (www-data). Directories will have permission 770 (read/write/execute for owner and group, nothing for others) and files will have permission 660 (read/write for owner and group, nothing for others).

This should change the way the /media/LUMIX filesystem gets mounted. I don't know of an easy and safe way to change this for all possible removable media (or all digital cameras).

---

### Post by salukibob on 2009-03-26
OK, for anyone thats interested, i've found the answer. Not in the most obvious place...

Apparently HAL asks the desktop-environment (whether GNOME, KDE, XFCE, etc) how to deal with the new plugged in device. Therefore, to fix this in GNOME, you simply need to open the gConf Editor (labelled Configuration Editor in the menu), and go to /system/storage/default_options/vfat, and amend the umask. 

I'm sure this makes sense to all the developers out there, but to a user this system seems unbelievably crazy. Say, for example you plug in a usb disk, and copy over some files to a shared harddisk. As the default permissions are set to user only, only the user that copied the files will be able to access them. What an unbelievable pain to have to remember to change permissions of these files each time you copy them!

GNOME developers, please look into this!

Rob

---

### Post by ftmichael on 2009-06-09
My boyfriend's having this trouble too - I'm not, even though we both use Jaunty, but we don't have the same model of camera.  Does the umask need to be changed from 077 to 644?  Will that give him **Owner: Read + write**, **Group: Read only**, and **Others: Read only**?

And why would 077 ever be a default?  Doesn't that mean that the Owner has no permission, but Group and Others both have read/write/execute?  That doesn't make any sense to me.

---

### Post by unutbu on 2009-06-09
Whenever you see the word "mask" in the context of permissions, know that it means the 7's complement of a permission. For example, ```


umask 077
```

means that every file created with this umask will have permission 700. In other words, to translate from the umask to the associated permission, you subtract the umask digit from 7.

Hope this helps.

---

### Post by ftmichael on 2009-06-09
Aha, I see.  So to get the permissions set to 644, I'd have to set **umask=133**?

---

### Post by unutbu on 2009-06-09
Yes, you've got it.

---

### Post by ftmichael on 2009-06-09
Excellent.  Thanks!  If it doesn't work for some reason, I'm sure you'll hear from me. :P

---

