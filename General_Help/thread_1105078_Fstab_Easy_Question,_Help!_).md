---
title: "Fstab Easy Question, Help! :)"
date: 2009-03-24
forum: General Help
---

### Post by Deathray on 2009-03-24
When I issue the command: sudo mount -t ntfs /dev/sda1 /ftpserver/
it works perfects, all users can read/right to this volume. How do I edit /etc/fstab to automatically mount this partition every boot without the command sudo mount -t ntfs /dev/sda1 /ftpserver/ ?
My current ftstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9af1eeb5-ffc5-4eeb-823a-33b20afd7ebd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0bc86938-9900-473e-8a8d-af7c196e60ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Keep in mind that I want to mount this partition before logging in, because the vsftp daemon has to be able to access it! :)

---

### Post by kanikilu on 2009-03-24
I think something like this should work:

```
/dev/sda1 /ftpserver ntfs-3g defaults,locale=en_US.utf8 0 0
```

Although, using it's UUID may be a better idea. If you want to do that, you can get the UUID by doing:

```
ls -l /dev/disk/by-uuid/ | grep sda1
```

If you want to use that, just change **/dev/sda1** to **UUID=###** (replace "###" with the number for your partition).

However you edit it, I always recommend that people run the following to make sure there are no errors in fstab: ```
sudo mount -a
``` *make sure sda1 is not already manually mounted before doing this

// Edit - Just noticed you are not in the US, you can probably remove that "locale=en_US.utf8" if necessary...

---

### Post by Deathray on 2009-03-24
> **kanikilu said:**
> I think something like this should work:

```
/dev/sda1 /ftpserver ntfs-3g defaults,locale=en_US.utf8 0 0
```

Although, using it's UUID may be a better idea. If you want to do that, you can get the UUID by doing:

```
ls -l /dev/disk/by-uuid/ | grep sda1
```

If you want to use that, just change **/dev/sda1** to **UUID=###** (replace "###" with the number for your partition).

However you edit it, I always recommend that people run the following to make sure there are no errors in fstab: ```
sudo mount -a
``` *make sure sda1 is not already manually mounted before doing this

// Edit - Just noticed you are not in the US, you can probably remove that "locale=en_US.utf8" if necessary...

Thanks a lot for the help mate, I really appreciate it! I'm sure I could of solved the problem by researching a bit more myself, but I just got so confused because many of the guides are for older versions of ubuntu and/or require a user interface to do and many of my attempts didn't work out.

I was wondering what exactly the locale= parameter did because my OS is in English but I am in fact living in Denmark with a Danish keyboard. So I just researched it for anyone interested. Basically if you have a folder which has an "abnormal" character such as æøå in the file/folder name, you may have problems seeing the file/folder. So that is the purpose of setting the locale :) But I can't seem to find any official site of how to properly select the locale, anyone know? :)

---

