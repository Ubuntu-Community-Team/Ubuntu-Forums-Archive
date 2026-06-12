---
title: "Automount problem"
date: 2006-08-03
forum: Desktop Environments
---

### Post by MasterZ on 2006-08-03
Hello, 

Today I tried to clean up my desktop of all the stuff mounted in /media. 
I unmounted everything and changed my fstab. 

I still have 1 icon on my desktop : "DVD-ROM Disc". 
That icon appear whenever I insert a CD/DVD in my internal IDE drive. 

The problem is that if I click on that icon to open nautilus, I see nothing on the CD-ROM. 
So that Icon just opens an empty folder... 
My /media directory is also empty. So I do not understand where that icon comes from. 

My IDE DVD-drive is /dev/hdc. I can mount it in /mnt/dvd and see the contents normally. 

Does someone know which process could make that icon appear on the desktop, so I can correct this behavior ? It is clearly linked to the real DVD drive, because it appears and disappears if I open/close the drive tray, but probably it points to something wrong. 


Thanks, 

MasterZ

---

### Post by MasterZ on 2006-08-04
UPDATE: 

I continue to do research on this issue, I thought that gnome-volume manager was in fault, but I sudo killed it and I still have the same behavior. 

That Icon appear whenever I put a disc in my drive and it opens nautilus in "burn://"... I do not see the contants of my disc.

I examined the logs I have in /var/log/ "syslog"; "kern.log"; "messages". They all display the same line when I insert a disc in the drive:
```
localhost kernel: [17179800.200000] cdrom: This disc doesn't have any tracks I recognize!

```

(remember that if I manually mount the disc (/dev/hdc) in /mnt/cdrom I can see the contents allright. so the disc is ok.)

I do not know where to search now. could someone give me a lead please?  :confused: 

Thanks,

MasterZ

---

### Post by msandersen on 2006-08-04
The stuff in /media is what gets mounted on the Desktop and under Places, AFAIK. Did you remove the cdrom entry in fstab? Seems your fstab doesn't specify the filesystem.
My fstab reads:
```
/dev/hdc        /media/cdrom0     udf,iso9660 user,auto   0       0
```

---

### Post by MasterZ on 2006-08-04
Hi, thanks for your answer, 

I did indeed try to remove the entry in fstab, but that doesn't change anything. 
The drive isn't mounted at all until I do it manually, yet that icon keeps appearing on my desktop. 

Here's the fstab line about my cdrom. I think it's pretty much ok :
```

/dev/hdc   /mnt/cdrom    udf,iso9660    user,noauto   0   0
```


Meanwhile I tried to find out what happen when I open/close my drive tray with the Ubuntu DVD inside and I found this ouput: 

```

$ lshal -ml

Start monitoring devicelist:
-------------------------------------------------
*** lshal: device_removed, udi='/org/freedesktop/Hal/devices/volume_empty_dvd_plus_rw'
*** lshal: device_added, udi='/org/freedesktop/Hal/devices/volume_empty_dvd_plus_rw'
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-system-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'as'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Eject'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.udi = '/org/freedesktop/Hal/devices/volume_empty_dvd_plus_rw'  (string)
  volume.disc.capacity = 4700372992  (0x1182a0000)  (uint64)
  volume.disc.is_rewritable = true  (bool)
  volume.disc.is_appendable = false  (bool)
  volume.disc.is_blank = true  (bool)
  volume.disc.has_data = false  (bool)
  volume.disc.has_audio = false  (bool)
  volume.disc.type = 'dvd_plus_rw'  (string)
  volume.size = 4700372992  (0x1182a0000)  (uint64)
  volume.num_blocks = 9180416  (0x8c1500)  (int)
  volume.block_size = 2048  (0x800)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = false  (bool)
  volume.mount_point = ''  (string)
  volume.label = ''  (string)
  volume.uuid = ''  (string)
  volume.fsversion = ''  (string)
  volume.fsusage = ''  (string)
  volume.fstype = ''  (string)
  storage.model = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_604072'  (string)
  block.is_volume = true  (bool)
  block.minor = 0  (0x0)  (int)
  block.major = 22  (0x16)  (int)
  block.device = '/dev/hdc'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_604072'  (string)
  linux.sysfs_path_device = '/sys/block/hdc/fakevolume'  (string)
  linux.sysfs_path = '/sys/block/hdc/fakevolume'  (string)

```

I do not know anything yet about hal and how it works or how to configure it, but it says strange things like:
```
volume.disc.is_blank = true  (bool)
  volume.disc.has_data = false  (bool)
```

This is not true at all and if I 
```
sudo mount /dev/hdc /mnt/cdrom
```
I can see the disc contents. So where does that wrong information come from? 

Some ideas ? 
MasterZ

---

### Post by MasterZ on 2006-08-04
ok, I found the source of the problem :p : 

It is due to that particular DVD that I had in the drive at boot time. I had screwed up my hal automount in some way. 

I removed the disc and rebooted. I'm now able to automount any DVD/CD but not that one. 
However I'm still able to mount it manually and see the contents. 

That DVD is the original from the game "Heroes of might and magic V". I know there is some copy protection on it (Securom I think) and it might be the cause of the problem. 

If I insert any other DVD, it is auto-mounted and I see this if I do "mount -l":
```

/dev/hdc on /mnt/cdrom type iso9660 
```

If I insert the protected "HOMM_V" DVD, it is not mounted and I get the following in /var/log/messages : 
```
localhost kernel: [17180511.336000] Unable to identify CD-ROM format.
```

If I then mount that "HOMM_V" DVD, manually, I see this f I do "mount -l":
```
/dev/hdc on /mnt/cdrom type udf
```

So maybe the protection make it so that the DVD is seen as 'udf format'. (anyone has seen that before?)

Then my following question is : 
How do I enable automount of udf volumes in hal ? is there any configuration utility/file  ? 

Thanks again, 

MasterZ

---

### Post by msandersen on 2006-08-05
> So maybe the protection make it so that the DVD is seen as 'udf format'. 
Could well be. Music CDs have the same shit. I hadn't bought a CD in ages, and when I did, it turned out to have copy protection, so my old Sony CD player couldn't play it, since the scheme breaks the CD standard. They try all sorts of tricks. One of them were even known to wreck the CD-ROM drive of early G3 iMacs.
Maybe the HAL works a little different from the mount command, and hence doesn't detect the protected disk. Might be worth a bug report.
Your reasons are your own, but why move things to *mnt*? Distros like Ubuntu are deliberately deprecating it in favour of *media*. Does it still appear under *Places*?

---

### Post by MasterZ on 2006-08-05
Hi,

I think you're right, I'll probably fill up a bug report for that one. 

To answer your question, I'm a bit new to ubuntu and I thought that removing the things from /media to put them into /mnt was the only way to get rid of the icons on the desktop. I recently learned that there was a nautilus option for that. ](*,) 

But even in /mnt, the cd still appears in Places. 

MasterZ

---

### Post by msandersen on 2006-08-06
It's a good thing that the CD still appears in places even when mounted in /mnt

As you may have found out, the option to turn icons on the desktop off isn't obvious, it's among the many configs that has been kept out of the preferences etc to avoid overcrowding it and keeping a user-friendly interface. Everything else has been put into the Gnome configuration editor. I think Ubuntu, or maybe it's Gnome 2.14 itself, hides it by default, but it's in **Applications -> System Tools -> Configuration Editor**
If not there, it can be made available through the **Applications Menu Editor**, I believe it is simply a matter of ticking the box to display it, as thje entry should already be there. Else using **gconf-editor** in a terminal will start it.
The options for the Desktop, since it it controlled byu the Nautilus file manager, just as the Windows desktop is controlled by Windows Explorer, can be found under 
**apps -> nautilus -> desktop** untick **volumes_visible**

---

### Post by t0maz on 2006-08-21
Hello,

Today I tried to put in a specific DVD in my drive with the UDF file format but it didn't mount. I could mount it myself (as root; not as user) though. I found out it was in the UDF filesystem format but the DVD I'm trying doesn't have any copy protection. I'm pretty sure for some reason Ubuntu (or a HAL thing; or a gnome thing) doesn't automount UDF formatted discs. Do you think this is worth a bug report somewhere? And if yes -- where can I do that?

Regards,
Thomas

---

### Post by Atomic Dog on 2006-08-28
My install of Ubuntu 6.06 would not mount UDF discs.

I learned that even though in fstab you should be able to pass multiple parameters (ex: udf,iso9660) only the last parameter will actually work.
For example: ```
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
will yield only iso9660 disks to be read & mounted.

By remming out the above line and replacing with:
```
/dev/scd0       /media/cdrom0   auto user,noauto     0       0
```
was I able to mount UDF and iso9660 discs & dvd's

---

