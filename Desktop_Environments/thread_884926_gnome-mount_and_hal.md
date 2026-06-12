---
title: "gnome-mount and hal"
date: 2008-08-09
forum: Desktop Environments
---

### Post by echo6 on 2008-08-09
I'm trying to configure gnome to mount removable media/storage as read only.
In /etc/hal/fdi/policy/preferences.fdi I have the following 
```
  <device> 
    <match key="block.is_volume" bool="true">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.ro" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noexec" type="bool">true</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.ro" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noexec" type="bool">true</merge>
        </match>
    </match>
  </device>
```
Automount works great, but will not adhere to this policy setting.  I would be grateful for any solutions or pointers to **good documentation** that would explain how best to achieve this!

As I understand it, udev handles device detection and hands it over to hal but also gnome-mount has a say in which mount options are used,  but I can not find how this should be configured.  Oh! yes I have also used gconf-editor with the storage keys to force various filesystem options, e.g. vfat/ntfs, as read only,  even with removable media is still mounted read-write.

---

### Post by NoelJB on 2009-08-13
See [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/319061](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/319061)

I could never get HAL to work, but since HAL is going away, I wrote a udev rule to do the deed.  In my case, I wanted noatime, in your case you would add "ro" as the remount option.

---

### Post by echo6 on 2009-10-03
Adding the following will work for mmc by editing the /etc/hal/fdi/policy/preferences.fdi 

```
<match key="storage.bus" string="mmc">
<merge key="storage.automount_enabled_hint" type="bool">false</merge>
</match>
```

Thanks to thefuf on another forum for posting this solution.

---

