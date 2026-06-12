---
title: "Unable to access folders"
date: 2009-12-16
forum: Desktop Environments
---

### Post by ackt83 on 2009-12-16
Hi there,

I am unable to access any folder via Places

For example when i click Places -> Home Folder, it will state "Opening Root" and close by itself.

When i type Nautilus into the terminal, i got the below results:

 [FONT=&quot]root@vps:~# nautilus
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "Generic Event Extension" missing on display ":1.0".
Xlib:  extension "Generic Event Extension" missing on display ":1.0".
Xlib:  extension "Generic Event Extension" missing on display ":1.0".

(nautilus:31851): GVFS-RemoteVolumeMonitor-WARNING **: remote volume monitor with dbus name org.gtk.Private.HalVolumeMonitor is not supported

(nautilus:31851): GVFS-RemoteVolumeMonitor-WARNING **: remote volume monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor is not supported

** (nautilus:31851): WARNING **: Failed to initialize hal : (null)

process 31851: Attempt to remove filter function 0x2b71acecedf0 user data 0x1ee84730, but no such filter has been added
libhal.c 3126 : LibHalContext *ctx is NULL
Segmentation fault
root@vps:~# 

Any advise is greatly appreciated :(
 
 [/FONT]

---

