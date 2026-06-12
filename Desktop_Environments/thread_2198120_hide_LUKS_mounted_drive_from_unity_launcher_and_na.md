---
title: "hide LUKS mounted drive from unity launcher and nautilus (ubuntu 12.04)"
date: 2014-01-07
forum: Desktop Environments
---

### Post by surfer on 2014-01-07
i post this here because i had to search for a while in order to find a working solution and there is a (closed) thread [here]("http://ubuntuforums.org/showthread.php?t=2048086") that was not answered.

the problem is the following:
my installation has a LUKS encrypted home drive. this drive is mounted at boot-time as it should. when i log in, i see the home partition just as a removable drive in the unity launcher. it also appears in nautlius as a removable drive with the unmount icon (i have no permissions to unmount it as regular user so there is no point in having that there).
here is how the drive can be hidden from the unity launcher and from nautlius.

first, find out the UUID of the LUKS partition you want to hide
```
$ cat /etc/crypttab
```

then create a udevd rule:
```
$ sudo nano /etc/udev/rules.d/99-hide-disks.rules
```
with the contents
```
# /etc/udev/rules.d/99-hide-disks.rules

ENV{ID_FS_UUID}=="uuiduuid-uuid-uuid-uuiduuiduuiduuidu",ENV{UDISKS_PRESENTATION_HIDE}="1"

```
(the UUID from above has to be inserted instead of the uuiduuid... string).

reloading the rules may not be necessary but can be tried:
```
$ sudo udevadm control --reload-rules
$ sudo udevadm trigger
```

that works for me in ubuntu 12.04 LTS precise pangolin.

---

### Post by boltronics2 on 2014-02-25
Excellent post - thanks! Worked for me on Debian GNU/Linux Wheezy.

I'll also point out a link stating that newer releases may require UDISKS_IGNORE  instead of UDISKS_PRESENTATION_HIDE.

Source: [http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/](http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/)

---

### Post by surfer on 2014-02-25
thanks for the update! i may be grateful for your post when i install trusty in the near future.

---

