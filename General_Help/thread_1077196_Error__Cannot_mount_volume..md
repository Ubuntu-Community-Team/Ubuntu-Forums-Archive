---
title: "Error : Cannot mount volume."
date: 2009-02-22
forum: General Help
---

### Post by kushal.7 on 2009-02-22
when i try to open the partition "softwares", it gives following error :

Cannot mount volume.
You are not privileged to mount the volume 'Softwares'.


one more error occur sometimes, i don't know that this is related to the above problem or not.

Unable to mount location :
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by lingwen on 2009-03-01
do you have multiple users on you're computer because if you do you may have to unmount the volume and mount it again on your user
that is the solution i found when i had this problem but i haven't got a clue why it does it

---

### Post by Xiong Chiamiov on 2009-03-01
To mount disks as a normal user, you need HAL, and HAL depends on DBUS, so yes, it has to do with that error.

What it is you're trying to mount?  If it's a permanent drive, it'd be better to put it in your fstab.  If so, paste the output here of
```

sudo fdisk -l

```

---

### Post by kushal.7 on 2009-03-01
my problem got solved after restarting the hal &dbus...

---

