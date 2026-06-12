---
title: "How can I revert changes to automount settings? 9.04"
date: 2009-06-15
forum: Desktop Environments
---

### Post by njgriffin on 2009-06-15
Hi There,

I've managed to make somewhat of a horlicks of Ubuntu's automount by changing some of the settings for one of my drives.  

I was having difficulties getting it to mount rw for user. In what seemed like a good idea at the time, while i had the drive mounted I right clicked on the icon on the desktop and tried to change the settings for the next mount to enable it to be rw.  I think I changed them in the 'Drive' tab.

Now it will not mount at all i get the following error
'Cannot mount volume
Invalid mount option when attempting to mount the volume"

I can mount other drives and the pesky one in question still shows up in places.

Where are these changes kept so that I can revert them back?

There is nothing in fstab.  Been rooting about in the file system but am really just groping in the dark.

Been Googling for ages and can't seem to find anything about where these settings are stored.

Any pointers much appreciated.

NjG

---

### Post by cariboo on 2009-06-15
Look in ~/.gconf/system/storage/volumes for a subdirectory with a name like:

```
_org_freedesktop_Hal_devices_volume_**uuid_5F3A5E5E63454964_0**
```

your uuid, the part in bold, will be different, delete the subdirectory to get your system back to normal.

Thanks unutbu

edit: ~ is a linux shortcut for /home/<user>

---

### Post by njgriffin on 2009-06-20
cariboo907

Apologies for the tardy reply. Only now had a chance to get a look at it. Many thanks that has it all sorted out.

Kind regards,

N

---

