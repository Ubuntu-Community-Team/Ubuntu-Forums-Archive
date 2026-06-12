---
title: "Mount point problem"
date: 2009-04-23
forum: General Help
---

### Post by Suncoaster on 2009-04-23
In attempting to add an additional hard disk I have somehow stuffed up the mount point for the drive as I get the following message when I attempt to mount the drive.  See attached screenshot.

Any help would be appreciated.  David

---

### Post by Tim Sharitt on 2009-04-23
Did you set the mount point in nautilus (Properties > Volume tab)? If so, what did you enter.

If that's not the case, what did you change to get the volume to mount?

---

### Post by Suncoaster on 2009-04-23
Yes I did, and I think I entered /work, but I am not sure if it was "work" but I remember I entered the "/".

David

---

### Post by Tim Sharitt on 2009-04-23
The mount point on the volume tab is the mount point under /media which will be used. For example, if you enter just 'work' then the volume will be mounted at '/media/work'.

 You can not use "/" in the mount point name (hence the error). If you would like to mount the volume at '/work', you'll likely need an entry in /etc/fstab.

If you would like to look into using fstab, look here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you have any other questions, feel free to ask. :)

---

### Post by Suncoaster on 2009-04-23
Thank you for the link, I will check it out.  In the meantime how do I remove the '/' in the label.  I checked /media and the drive is not listed there, and unless I can mount the drive I do not have access to the properties/volume tab.

David

---

### Post by Tim Sharitt on 2009-04-23
You can try to manually mount the drive under media and see if you can to the volume tab to remove the "/".

First you need to create a directory to mount the drive to. Open a terminal and do:
```
sudo mkdir /media/mount_point
```
(mount_point can be any name you choose)

Now mount the drive, you will need to know name of the device you want to mount and the file system (ask if you don't know and we can figure it out).

```
sudo mount -t [type of file system] /dev/sdXY /media/mount_point
```

Where X is the drive and Y is the partition.

After that is done, go to the volume tab of the properties window in nautilus.

---

### Post by Suncoaster on 2009-04-23
Tim,  Thank you all is now OK.:guitar:   That's what I like about these forums, there is always someone willing to help with your problems.

Regards
David

---

