---
title: "speed up automount"
date: 2009-05-16
forum: General Help
---

### Post by rock4christ on 2009-05-16
is there a way to speed up the process of automounting a ntfs partition at bootup?(on the same hard disk as my ubuntu 9.04)

---

### Post by taurus on 2009-05-16
What do you mean by speeding up?  Do you have an entry in /etc/fstab to mount that ntfs partition?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by rock4christ on 2009-05-16
yes, I have it. Im wanting to make the automount go faster(to speed up my boot time)

---

### Post by rock4christ on 2009-05-17
bump

---

### Post by rock4christ on 2009-05-17
anyone?

---

### Post by charliehorse55 on 2009-05-17
You could remove the mount from fstab, and have it has a login cron task. 

This would shorten boot process, but of course you would not be able to access any files on the drive until 20 seconds after logging in. If you're just using the drive to playback media, this is probably a good idea. If you have other files that the system needs, this will not work.

---

### Post by rock4christ on 2009-05-17
> **charliehorse55 said:**
> You could remove the mount from fstab, and have it has a login cron task. 

This would shorten boot process, but of course you would not be able to access any files on the drive until 20 seconds after logging in. If you're just using the drive to playback media, this is probably a good idea. If you have other files that the system needs, this will not work.

it has my wallpaper and my torrents(meaning deluge will likely hiccup if I do that)

---

### Post by rock4christ on 2009-05-18
I suppose if i delayed deluge by 50 or so sec it'd work.

how would I:
1. delay deluge
2. remove the automount I currently have on sda2
3. add it as a chron task

---

### Post by sandy8925 on 2009-05-18
I can answer question 2.
Just delete the line corresponding to the ntfs partition from the /etc/fstab file.

Example:

If /dev/sda1 is your ntfs partition and it is being automounted then there should be a line starting with or below /dev/sda1.

Just delete that line. However BE CAREFUL WHILE REMOVING THAT LINE.

---

### Post by rock4christ on 2009-05-18
change
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                      0  0  
# / was on /dev/sda3 during installation
UUID=fe9b8957-fa6c-419e-b662-e76ed8f6cf10  /              ext4         noatime,nodiratime,errors=remount-ro    0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  

/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000,user  0  0  
```

to

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                      0  0  
# / was on /dev/sda3 during installation
UUID=fe9b8957-fa6c-419e-b662-e76ed8f6cf10  /              ext4         noatime,nodiratime,errors=remount-ro    0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  
```

right?


how would I delay deluge by ~50 sec and set up the mount as a chron login task?

---

### Post by rock4christ on 2009-05-18
bump

---

