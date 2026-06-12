---
title: "Mount in read only"
date: 2008-02-07
forum: Desktop Environments
---

### Post by stefanolmo on 2008-02-07
How can I mount removable media in read only mode automatically?
After that, can I change the permission in rw without removing the media?

Thanks!

---

### Post by kevstar31 on 2008-02-09
what command do you use to manually mount your removable media?

---

### Post by kidders on 2008-02-10
> **stefanolmo said:**
> How can I mount removable media in read only mode automatically?
After that, can I change the permission in rw without removing the media?

Thanks!

Hi there,

This is quite a frustrating problem. It's *supposed* to be easy, but when I gave the solution a quick try before posting it, I couldn't make it work. In theory, all you need to do is set up a HAL policy governing removable media, something along the lines of ...```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
     <device>
          <match key="volume.fsusage" string="filesystem">
               <match key="@block.storage_device:storage.hotpluggable" bool="true">
                    <match key="@block.storage_device:storage.removable" bool="true">
                         <merge key="storage.policy.mount_option.ro" type="bool">true</merge>
                    </match>
               </match>
          </match>
     </device>
</deviceinfo>
```However (for some reason that's totally beyond me), my Linux box recognises the read-only directive, and then proceeds to completely ignore it. This aspect of HAL's behaviour is so poorly documented, I'm having a tough time figuring out why that is, but since it's the most "correct" solution, I suggest trying it first ... perhaps your system won't have the same desire to irritate you as mine seems to have!

If you *can* get it to work, re-mounting in read/write mode is a matter of...```
mount -o remount,rw /device/path/here
```If HAL won't cooperate for you though, things become a little hacky. Essentially, you'll have to find a way to apply a specific mount option to devices you don't know the names of, which gets a bit messy.

One quick, ugly-as-hell solution would be to set up /etc/fstab rules for imaginary devices like /dev/sdd1, /dev/sdd2, /dev/sde1, etc. that all specify the "ro,noauto" mount options.

Another (more realistic) possibility would be to suffer read/write mounts for removable devices you don't already own, and hot-wire your Linux to treat the ones it *does* know about differently. For example, you could use udev rules to configure an iPod to appear at /dev/ipod, /dev/ipod1, /dev/ipod2, etc., and add a line to /etc/fstab along the lines of...```
/dev/ipod2 /media/ipod hfsplus ro 0 0
```By doing the same sort of thing with /dev/camera, /dev/backup (or whatever you happen to have), your Linux would never mount anything it already knew about in read/write mode by default.

Of course, the best solution would be to try to figure out how to make HAL do what it was *designed* to do. Failing that, the next best option really depends on why you want filesystems mounted in read only mode in the first place.

---

