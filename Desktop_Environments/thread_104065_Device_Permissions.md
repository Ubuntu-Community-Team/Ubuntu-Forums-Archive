---
title: "Device Permissions"
date: 2005-12-15
forum: Desktop Environments
---

### Post by gilgongo on 2005-12-15
This must be a common question, but I can't see to find a straight answer.

If you need to write to a device, and you don't have permission to do so (in my case it's /dev/raw1394) do I really have to start the relevant app as root?

If I change the permissions of the device to give me write access, something sets it back again (lord I hate it when that happens  - I changed it for a reason, dadnabbit!)

Thanks for any tips.

---

### Post by tlc on 2005-12-15
Try
```
chattr +i /dev/raw1394
```
after you've chmodded it. This should lock it. Unlock with
```
chattr -i /dev/iee1394
```

Or it could be the other way round, but you get the idea.

I had to do this to my /etc/resolv.conf to stop dhcpd overwriting it with rubbish at every boot. It might preserve your desired permissions too.

---

### Post by gilgongo on 2005-12-15
Ah OK, thanks. 

Feels like there ought to be a better way than setting attributes on stuff like this though seeing as 99.9999% of everyone using Ubuntu to get video off a camcorder will **not** be wanting to do it as root.

---

### Post by psusi on 2005-12-15
This will not work.  chatter sets extended attributes on the ext2/3 filesystem.  The problem is that /dev is a tmpfs, so it is forgotten every time you shut down, and recreated every time you boot up.  

Usually the device nodes are set to give the owning group write access, and are given a sane owning group.  Add yourself to that group.  

[QUOTE=tlc]Try
```
chattr +i /dev/raw1394
```
after you've chmodded it. This should lock it. Unlock with
```
chattr -i /dev/iee1394
```

Or it could be the other way round, but you get the idea.

I had to do this to my /etc/resolv.conf to stop dhcpd overwriting it with rubbish at every boot. It might preserve your desired permissions too.[/QUOTE]

---

### Post by s_p_a_r_k_y on 2005-12-15
as root you should be able to set the user/group which has access to the devices. So create a new group or add an existing group as the group of the devices

chown user:group /dev/device

where you leave user as root and then change the group name to something else. Add yourself to that group as root

adduser yourUserName theGroupYouWantToBeAPartOf

Then make sure that the group has read/write permissions on it

chmod 775 /dev/device

---

### Post by psusi on 2005-12-15
Again, this won't work because everything in /dev goes away when you shut down and will be recreated when you boot up again.  You need to add yourself to the group that already owns the device.  

[QUOTE=s_p_a_r_k_y]as root you should be able to set the user/group which has access to the devices. So create a new group or add an existing group as the group of the devices

chown user:group /dev/device

where you leave user as root and then change the group name to something else. Add yourself to that group as root

adduser yourUserName theGroupYouWantToBeAPartOf

Then make sure that the group has read/write permissions on it

chmod 775 /dev/device[/QUOTE]

---

### Post by soulestream on 2005-12-15
/dev/raw1394 is in the "disk" group. try adding yourself to it.


or edit the udev rule to change permissions to the ones you want

/etc/udev/rules.d/020_permissions.rules you should be able to add MODE="0666"

to the end of KERNEL=="raw1394",      GROUP="disk"

*NOTE. i havent tried this, as I just started playing with udev, but in theory. ;) 

lastly

[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220) <- this makes it executable at boot.


soule

---

