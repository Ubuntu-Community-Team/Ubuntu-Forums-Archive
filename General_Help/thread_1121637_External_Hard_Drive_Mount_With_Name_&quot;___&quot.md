---
title: "External Hard Drive Mount With Name &quot;___&quot;..."
date: 2009-04-10
forum: General Help
---

### Post by jiapei100 on 2009-04-10
Seriously urgent.
Can anybody help?


No idea of why my WD 500 Giga external hard drive was mounted as

"/media/Elements_"

rather than 

"/media/Elements"

this morning.

After checking and modifying /etc/mtab , I came to even worse condition:

In the folder "/media", I have

Elements
Elements_
Elements__
Elements___
Elements____


and finally, the external hard drive mounted to Elements____



Can anybody help out?

Please...


Rgds
JIA

---

### Post by jiapei100 on 2009-04-10
What I have to do now is just umount "Elements____" every time after rebooting.

Then, mount my device to "Elements"

This is really stupid.


I modified /etc/mtab and /etc/mtab~ both, but it doesn't help to solve the problem


I think there must be some place on my external hard drive or in /home/account/.* , which actually remembers the last record, or somewhere else.


Seriously annoying. Can anybody help please.


Rgds

JIA

---

### Post by drs305 on 2009-04-10
The system keeps adding another "_" to the name when it tries to mount on "Elements" and thinks there is something else mounted there. So the default is to add "_"s until it finds one that doesn't exist.

First, umount the device and, *after checking these folders are empty*, delete them all. 

Have you added this device to /etc/fstab or done anything manually to effect where it is mounted? What format is it? You can also check gconf-editor to see if you have any special mount options for that specific format:
```
gconf-editor /system/storage/default_options
```

Also try mounting it, noting the mount point, unmounting it and then mounting it again. Does it add the "_" again?

---

### Post by jiapei100 on 2009-04-11
Thanks for your kind help!!
Yes, now, I deleted all the folders, including those with"__" and even the one named "Elements" without even a single "_".

However, I still fail to automatically mount it. The only way to work around this is to manually mount it.

There is nothing reflected in fstab and mtab. I mean, whenever I plugin my USB external hard drive, the system seems to be able to detect the hard drive, but fail to mount it for sure.

The message I've got now is:

in the first window
"
Invalid mount option when attempting to mount the volume
"

in the second window
"
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
"



What should I do now?


Anyway, mount it manually and start working first.


Rgds
JIA

---

### Post by drs305 on 2009-04-11
> **jiapei100 said:**
> What should I do now?
Anyway, mount it manually and start working first.


I guess we are making some progress at least.

1. You might try reinstalling gnome-mount. I don't have high hopes but it may fix it:
```

sudo apt-get update
sudo apt-get install --reinstall gnome-mount

```

2. You didn't say what type of format it is or whether you took a look at gconf-editor. I would go to the format you are having problems with and reset the values:
```
gconf-editor /system/storage/default_options
```
Highlight the format type and then in the right pane right click any listing and choose "Unset" to restore the default values.

3. Unless you are absolutely sure you don't have an improper entry in fstab, post:
```

cat /etc/fstab

```

---

### Post by Gen2ly on 2009-04-11
Don't edit /etc/mtab the system  writes that to know what drives are mounted.

---

### Post by jiapei100 on 2009-04-12
> **drs305 said:**
> I guess we are making some progress at least.

1. You might try reinstalling gnome-mount. I don't have high hopes but it may fix it:
```

sudo apt-get update
sudo apt-get install --reinstall gnome-mount

```


Tried, but failed. It doesn't work for me.

> 
2. You didn't say what type of format it is or whether you took a look at gconf-editor. I would go to the format you are having problems with and reset the values:
```
gconf-editor /system/storage/default_options
```
Highlight the format type and then in the right pane right click any listing and choose "Unset" to restore the default values.


checked already. I'm using Ubuntu 8.10 which is in format "ext3", and the external hard drive is also "ext3".
The interesting is in "/system/storage/default_options", there are only
hfs
iso9660
ntfs
ntfs-3g
udf
vfat

Should there be something like "ext3" ?

and in "/system/storage/volumes/_org_freedesktop_Hal_devices_volume_uuid_*******"

there are three items:
fstype_override     ext3
mount_options       [rw,nosuid]
mount_point         Elements

Any suggestions? 

> 
3. Unless you are absolutely sure you don't have an improper entry in fstab, post:
```

cat /etc/fstab

```


I'm sure that I don't have anything wrong in fstab. 






The problem keeps, no solution yet. Two dialogs jump out:

"
Cannot mount volume.
Invalid mount option when attempting to mount the volume 'Elements'
"

and
"
Unable to mount Elements
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
"


Thanks for you help and waiting for your reply.

Best Regards
JIA

---

### Post by drs305 on 2009-04-12
My guess is there are conflicts as to what format the device/partition actually is. 
With the hard drive plugged in, check the format:
```
sudo bklid -c /dev/null
```
Check the results with fstab's entries.

In gconf-editor, I don't have any ext3 entries, so I would regard that as normal.

If the format of your external drive is correct, you might remove the entry from gconf-editor for this device. The "override" doesn't seem correct. I could see it listed as that if you are saying in fstab it is ext3 but in fact isn't or it's listed in fstab as something else but is in fact ext3. This entry can be reconstructed if necessary.

---

