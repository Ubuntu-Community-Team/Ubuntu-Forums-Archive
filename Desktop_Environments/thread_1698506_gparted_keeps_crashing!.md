---
title: "gparted keeps crashing!"
date: 2011-03-02
forum: Desktop Environments
---

### Post by MasterNetra on 2011-03-02
I'm was trying to part a USB drive so I could have some swap on it for the Ubuntu Image, I had successfully done so on another drive without issue and running Ubuntu or a variant of it on a USB drive with swap was noticeably faster when running in live-cd mode. So I wanted to do the same with this one. However I have some items on for storage purposes but I didn't think much of it and went a head and had gparted to pull out the free space for swap (it still had room for the Ubuntu image btw even after pulling 1GB for swap). However, during the process gparted simply crashed and now every time gparted starts it automatically crashes...

I tried to run it via terminal and got this:

```

======================
libparted : 2.3
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xb0a87a]
  15: /lib/libparted.so.0(+0x41337) [0xb42337]
  14: /lib/libparted.so.0(+0x42157) [0xb43157]
  13: /lib/libparted.so.0(+0x4344c) [0xb4444c]
  12: /lib/libparted.so.0(+0xe161) [0xb0f161]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xb129f2]
  10: /lib/libparted.so.0(+0x44ea5) [0xb45ea5]
  9: /lib/libparted.so.0(+0x450af) [0xb460af]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xb137d5]
  7: /usr/sbin/gpartedbin() [0x80900b6]
  6: /usr/sbin/gpartedbin() [0x809beb5]
  5: /usr/sbin/gpartedbin() [0x80c1dd2]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x710e42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0x26348f]
  2: /lib/libpthread.so.0(+0x5cc9) [0x1b8cc9]
  1: /lib/libc.so.6(clone+0x5e) [0x107469e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function probe_partition_for_geom() failed.

```
Also tried uninstalling gparted (using remove completely option in synaptic) then reinstalling, no change. Even used Ubuntu's format options to fully format the USB drive (after moving the storage stuff onto the system) and still nothing....no play from gparted in live-cd mode either...

**Update**
Apparently its the USB device, I removed it and inserted the other one to see if it will read, and it ran fine... The "free space" partitioned off on the other one seems to of been corrupted, doesn't look as if I can get this corrected in Ubuntu...unless there is some way to force a full wipe of the USB drive...

---

