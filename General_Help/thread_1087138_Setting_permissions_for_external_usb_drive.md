---
title: "Setting permissions for external usb drive"
date: 2009-03-04
forum: General Help
---

### Post by eteq on 2009-03-04
I have an external USB drive that I use with a laptop that is sometimes plugged in (e.g. at work) and sometimes not.  It consistently mounts with the same name, so something in Ubuntu knows what drive it is (despite the fact that it's sometimes /dev/sdb1, /dev/sdc1 , etc.).  

I would like to be able to set the permissions of this drive every time it is plugged in to allow a second user (someone who sometimes uses scp to copy files to the computer) to access the external drive.  

I've tried manually doing chmod or chown on the drive, and the permissions don't change... I've also tried manually mounting it to a new directory, but whatever I do, the permissions are always only for the my user name, and I can never let another user or group access it (except as root, which I don't want to allow).

So how do I do this?



(I'm running Intrepid)

---

### Post by mempman on 2009-03-04
> **eteq said:**
> I have an external USB drive that I use with a laptop that is sometimes plugged in (e.g. at work) and sometimes not.  It consistently mounts with the same name, so something in Ubuntu knows what drive it is (despite the fact that it's sometimes /dev/sdb1, /dev/sdc1 , etc.).  

I would like to be able to set the permissions of this drive every time it is plugged in to allow a second user (someone who sometimes uses scp to copy files to the computer) to access the external drive.  

I've tried manually doing chmod or chown on the drive, and the permissions don't change... I've also tried manually mounting it to a new directory, but whatever I do, the permissions are always only for the my user name, and I can never let another user or group access it (except as root, which I don't want to allow).

So how do I do this?



(I'm running Intrepid)

If you have this as an entry in your /etc/fstab file, then I think the difference is in either having the "user" vs. "users" option.  Also you need the "rw" option.

---

### Post by eteq on 2009-03-04
It's not in /etc/fstab - external USB devices aren't there because they often aren't connected, and the locations in /dev change depending on what order you plug them in.  And that's the whole problem... 

The relavent entry in /etc/mtab is:
/dev/sdb1 /media/ERIKBK vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

it already has rw... if I try to mount it as 

mount /dev/sdb1 /some/where /else -o rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=someotheruser,utf8,umask=077,flush

it mounts fine, but someotheruser still can't cd into the directory - ("permission denied" or whatever the error is)

---

### Post by mempman on 2009-03-10
> **eteq said:**
> It's not in /etc/fstab - external USB devices aren't there because they often aren't connected, and the locations in /dev change depending on what order you plug them in.  And that's the whole problem... 

The relavent entry in /etc/mtab is:
/dev/sdb1 /media/ERIKBK vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

it already has rw... if I try to mount it as 

mount /dev/sdb1 /some/where /else -o rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=someotheruser,utf8,umask=077,flush

it mounts fine, but someotheruser still can't cd into the directory - ("permission denied" or whatever the error is)

I think you need to add "users" to the list of mount options that you have provided above (i.e. directly after "flush").

---

### Post by eteq on 2009-03-11
I tried adding "users", but it still mounts as my user name and the root group (and if I try to change it, I get "chown: changing ownership of `test': Operation not permitted")

---

