---
title: "little help g"
date: 2009-03-15
forum: General Help
---

### Post by saeed_aae on 2009-03-15
I have two questions guys:
1°)How to delete files (and/or folders) using the Terminal.
2°)How to unmount media devices(CDs as well) using the Terminal.

Thanks in advance :)

---

### Post by drs305 on 2009-03-15
To remove files owned by you:
```

rm /path.to.file

```

To unmount:
```

umount /device
or 
umount /mount.point

```
Example: umount /dev/sdb1  or  umount /media/data
Note the spelling. You may need to use "sudo umount", depending on how it was mounted.

Added: You can unmount all non-system devices with "sudo umount -a"

---

### Post by saeed_aae on 2009-03-15
Thanks a lot man, works like a charm :p

---

### Post by Nano_ext3 on 2009-03-15
If you want to remove a folder and all its contents:

```
sudo rm -Rv FOLDER_NAME
```

Keep in mind, this will permanently delete the file, you should move the file to trash via the GUI File Manager if you plan on getting it back.

To Unmount follow this: 

 ```
sudo umount /dev/device_location
``` 

If you cannot unmount, due to a process using it , type "lsof /dev/device_location" in terminal where "device_location" is the location mount point of your device.  You can find this by running "sudo fdisk -l" in the terminal.  If you know the size of your drive in question its easy.  If not, and its a removable drive, open up the drive in your GUI File Manager, and click the "note pad icon" on the left side of the file manager.  Note the location for unmounting purposes.


Cheers!


-Nano

---

