---
title: "Thunar issue with dbus/udisks2 - delay on first start &amp; doesn't see mountable volumes"
date: 2021-06-04
forum: Desktop Environments
---

### Post by mewingatthemoon on 2021-06-04
So I noticed, as per title, Thunar takes about 20 seconds to start on my Surface Pro 3 after each login. Subsequent starts are fast as expected; however, Thunar's volume management doesn't work at all. USB devices are not auto-mounted or even shown on the list of mountable volumes. I can still mount them with udisksctl mount -b </dev/whatever>, and they will then show up in the list and be possible to *unmount *in Thunar, but that's it.

I notice a lot of this in .xsession-errors:

```

Error creating proxy: Error calling StartServiceByName for org.gtk.vfs.UDisks2VolumeMonitor: Timeout was reached (g-io-error-quark, 24)

```

But no idea what's causing that. Thoughts? My user is in the plugdev group so I don't think it's a groups issue.

---

### Post by TheFu on 2021-06-05
Maybe using autofs with a "--ghost" option would work better?  Just setup unique LABELs for each partition to be mounted and you can pick the location where it will be mounted and all configuration/performance options too.

/etc/auto.master:
```
- /etc/auto.Data --timeout=60 --ghost
```

In /etc/auto.Data :
```

/Data/usb_tv -nodev,nosuid,noatime,timeout=2,fstype=**ext4**     LABEL=USB_TV
/Data/250G -nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=**ntfs**,uid=1000,gid=1000,fmask=0002,dmask=0002  LABEL=250G
```

All that is left is to use any program you want to access the storage location.  **ls /Data/250G ** is sufficient. With the --ghost option, Thunar should see the top level so you can click on it. That will mount the storage, using whatever options specified.

Setup is just **sudo apt install autofs**, then edit the files like above. Autofs will mount and un-mount storage based on when files are open or not on it.  Takes a few minutes of inactivity for the umount to happen automatically.   If the file system isn't mounted, it is safe to remove from the USB port. All data was flushed to disk before.
After any config changes, just restart the *autofs* service.

Anyways, just another option to consider.

---

### Post by ajgreeny on 2021-06-05
This used to be a problem many years ago for thunar and I have just found one of the many notes that I keep which may help you overcome this behaviour, though I have not seen it myself for a very long time.
> 
Edit **/usr/share/gvfs/mounts/network.mount** and change it from:
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=[COLOR="#FF0000"]true[/COLOR]
```
to
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=[COLOR="#FF0000"]false[/COLOR]
```

it will make opening up thunar very quick again even for the first time.  If you want the smb browsing you just click on the network:/// link in thunar and it will then do the browsing search which takes a bit of time.
I have just looked at my version of this file and find that it already has false in that stanza, so perhaps that is now the default as I don't think I have edited it myself.

However, it appears that the slow behaviour you see is probably related to something else, though I never expect attached ; or have I misunderstood your situation?USB devices to mount at boot unless included in fstab

---

