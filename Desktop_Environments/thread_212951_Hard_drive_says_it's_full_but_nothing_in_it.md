---
title: "Hard drive says it's full but nothing in it"
date: 2006-07-10
forum: Desktop Environments
---

### Post by usp8riot on 2006-07-10
I made a fat32 partition with gpart and I can only copy like 300mb's to it until it says it's full. I click on 'view hidden files' and there's nothing more in there. wtf is up with it?

---

### Post by Paerez on 2006-07-10
Check:
System -> Administration -> Disks
and see how much free space is reported there, make sure it's correct.

---

### Post by usp8riot on 2006-07-10
I can't boot into KDE, so I'm using gnome interface. Now I can't see my files at all on my fat32 partition after I booted to windows to free the space on it. I've included an attachment of what Kdisk says. My new partition should be hdd and it doesn't show it yet konquerer shows it. Windows detects and reads and writes to it just fine even though it was formatted using gpart.

Update: KDE sees the drive, sees the size correctly, but says it's like 90% full even though it's only got about 1 gig of it's 10 gigs filled. And it doesn't show any files even though Windows sees them. Is there a hidden file somewhere? Does Ubuntu 6.06 not correctly ID fat32 partitions? Or am I just better off formatting the drive with another file system type?

Update again: So I reformatted it with qtpart but it won't mount it. It says 

"mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
Please check that the device is plugged correctly."

Any ideas anyone?

---

### Post by Paerez on 2006-07-10
it is not going to be /dev/hdd. As the error message shows, it is /dev/sda2.

After you partition, try refreshing the drives:
```
# sudo /etc/init.d/dbus-1 restart
```

Also, can you show me a screenshot of the partition program?

---

### Post by usp8riot on 2006-07-11
Thanks but I tried that. I tried manually editing the fstab file also. I tried to get a screenshot of qtpart but the alt+print button didn't work anymore for some reason so I was going to edit the pic but then after manually clicking the print screen program it didn't save it to the desktop like it said it was and refresh button wasn't working on my keyboard apparentl. 

I go to 'conquer my desktop' and look at the drives, like my sda2 drive which exists because it's showing it yet when I try to mount it I get

 "mount: mount point /media/sda2 does not exist
Please check that the device is plugged correctly."

No more problem with the KDE media manager since I upgraded to KDE 3.5.3 but it still some programs still won't see the drive. And they misconfigure the used space. I don't want to go back to Windows after a week of being happy with Kubuntu for the most part, but I'm considering it. I think I'll try formatting it with ext3 since I got the ext2/3 driver installed for Windows. Maybe that will work and I'll update in case anyone has to go through this.

Edit: The script you were giving me gave me obviously closes the mediamanager so that's what gave me the problem unless I rebooted. There's got to be a way to mount an ext3 or fat32 partition in kubuntu so i can see it and use it. wtf am I doing wrong?

Edit: Nevermind, I think I got it just using the mount command but having some trouble with file permissions and all. I'll figure it out one of these days.

---

### Post by Paerez on 2006-07-11
the mount command would be:
```
# sudo mkdir /media/sda2
# sudo mount -t vfat /dev/sda2 /media/sda2
```

the fstab line would be like:
```
/dev/sda2    /media/sda2    vfat    rw,users,umask=0000    0 0
```

hope that helps

---

### Post by usp8riot on 2006-07-11
Yes, I got it now. It seems to be some conflict between tutorials I've read of different versions of unix or linux or I'm just stupid. Thanks again.

---

