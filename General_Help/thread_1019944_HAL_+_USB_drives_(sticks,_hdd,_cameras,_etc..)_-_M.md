---
title: "HAL + USB drives (sticks, hdd, cameras, etc..) - Mount point"
date: 2008-12-23
forum: General Help
---

### Post by msamson on 2008-12-23
Hi folks,


I am trying to figure out HAL policies under ubuntu. After trying several options, i realized HAL was much more complicated and the ubuntu/hal doc is hard to find/incomplete.

What I am trying to achieve is to mount all USB volumes (that is, usb keys, hard drive, camera, ipod, etc) to a single mount point (or more, but let's do a single first).

I put this at /etc/hal/fdi/policy/gcc.fdi but it doesn't seem to do antyhing:
```
<device>
  <match key="block.is_volume" bool="true">
    <match key="storage.removable" bool="true">
      <match key="info.bus" string="usb">
        <merge key="volume.policy.desired_mount_point" type="string">gueststorage</merge>
      </match>
    </match>
  </match>
</device>
```


restarted HAL, rebooted the station and when i plug a usb device, it still mount with it's name.

So here's a few questions: 
where should i put the policy file (fdi)?
what is wrong i what i wrote?
if nothing above is wrong, why does a key mount let say as kingston and the other as memorex ?

Thanks for the help
Martin Samson

---

### Post by dcstar on 2008-12-23
> **msamson said:**
> 
What I am trying to achieve is to mount all USB volumes (that is, usb keys, hard drive, camera, ipod, etc) to a single mount point (or more, but let's do a single first).
.......

Use Volume Labels.

---

### Post by msamson on 2008-12-24
In the use case, we won't be able to change the volume label of thousands of different usb drives, even less when they are not our property.

I know HAL can mount to a specified mount point based on matches as described by the fdi file I put in the first post.

Another thing to consider is we are not using Gnome as the window manager.

Bare X. A python must starts when the key is inserted (HAL can also do this)

---

### Post by msamson on 2008-12-24
Found part of the solution.

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="block.is_volume" bool="true">
      <match key="@block.storage_device:storage.hotpluggable" bool="true">
        <merge key="volume.policy.desired_mount_point" type="string">guest</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```


now just gotta find how to execute code :)

---

### Post by msamson on 2008-12-24
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
 <device>
   <match key="block.is_volume" bool="true">
     <match key="@block.storage_device:storage.hotpluggable" bool="true">
       <merge key="volume.policy.desired_mount_point"
type="string">guest</merge>
       <append key="info.callouts.add" type="strlist">beep -f 77</append>
     </match>
   </match>
 </device>
</deviceinfo> 
```


info.callouts.add type = strlist.

---

