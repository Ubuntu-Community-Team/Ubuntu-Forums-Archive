---
title: "Lucids upgrade to 4.4 beta breaks disk mounting?"
date: 2009-12-29
forum: Desktop Environments
---

### Post by Ubuntiac on 2009-12-29
**Moved discussion for this thread to [[COLOR="Blue"]here[/COLOR]](http://ubuntuforums.org/showthread.php?p=8733877) as per falconindy's suggestion.**

Ever since the KDE 4.4 beta packages came in, I've been unable to mount drives either with the new "removable devices" section in system settings (although my drives are IDE/SCSI) or in Dolphin. I just get an error:

An error occurred while accessing 'Seagate15tb', the system responded: org.freedesktop.Hal.Device.Volume.PermissionDenied: Refusing to mount device /dev/sda1 for uid=1000

It's obviously permissions of some description, but I'm wondering how one would fix this. Do I need to add my user to the "disk" group or something like that?

I'm on Kubuntu Lucid AMD64 with KDE 4.4 Beta 2
with 1 ide ext4 partition, 1 ide connected ntfs partition and 1 scsi connected ntfs partition. All fail in the same way.

---

### Post by falconindy on 2009-12-29
Lucid forum is [over here](http://ubuntuforums.org/forumdisplay.php?f=377).

Look through /etc/hal/fdi/policy files to understand who has access to mount volumes. It may be as simple as adding yourself to the disk or storage group.

---

### Post by SuperSonic4 on 2009-12-29
> **Ubuntiac said:**
> Ever since the KDE 4.4 beta packages came in, I've been unable to mount drives either with the new "removable devices" section in system settings (although my drives are IDE/SCSI) or in Dolphin. I just get an error:

An error occurred while accessing 'Seagate15tb', the system responded: org.freedesktop.Hal.Device.Volume.PermissionDenied: Refusing to mount device /dev/sda1 for uid=1000

It's obviously permissions of some description, but I'm wondering how one would fix this. Do I need to add my user to the "disk" group or something like that?

I'm on Kubuntu Lucid AMD64 with KDE 4.4 Beta 2
with 1 ide ext4 partition, 1 ide connected ntfs partition and 1 scsi connected ntfs partition. All fail in the same way.

Methinks /etc/PolicyKit/PolicyKit.conf is to blame.

I did the following

 If you move it

```
cd /etc/PolicyKit
sudo -i 
mv PolicyKit.conf PolicyKit.conf.bak
nano PolicyKit.conf

```

And paste in the following

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
     <define_admin_auth group="**wheel**"/>
</config>
```

replace *wheel* with your user if you don't want all of wheel group to have the power[/code]

exit nano

```
touch PolicyKit.conf
```

---

### Post by Ubuntiac on 2010-01-27
Still no improvement after trying that PolicyKit.conf change and upgrading to the latest RC of KDE. :'(

Moved discussion for this thread to [[COLOR="Blue"]here[/COLOR]](http://ubuntuforums.org/showthread.php?p=8733877) as per falconindy's suggestion.

---

### Post by overdrank on 2010-01-27
Thread closed as link is given for new thread. :)

---

