---
title: "DELL Inspiron 530 CAN'T USE THE INTEL VIDEO DRIVER"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by gcwxj on 2007-07-27
I JUST RECEIVED MY NEW DESKTOP, WHICH IS PRELOADED UBUNTU 7.0.4. I FELT VERY FRUSTRATED FOR THE VIDEO CARD CONFIGURATION. I INSTALLED xserver-xorg-intel driver BUT IT COULD NEVER WORKS. IF I CHANGE THE DEVICE TO "INTEL" OF THE xorg.conf THE GDM WILL NOT START. I COULD ONLY USE THE "vesa". WHO CAN HELP ME FOR THE VIDEO CARD CONFIGURATION. THANKS A LOT!

---

### Post by gcwxj on 2007-07-27
When I change the device to "intel" in the xorg.conf file, the error information is stated below:

(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
for allocation.  Using pre-allocated memory only.
(==) intel(0): VideoRam: 7164 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with tiled buffers and 
               small DRI memory manager reservation:
(II) intel(0): Allocating 5340 scan(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
for allocation.  Using pre-allocated memory only.
(==) intel(0): VideoRam: 7164 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with tiled buffers and 
               small DRI memory manager reservation:
(II) intel(0): Allocating 5340 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
               small DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(WW) intel(0): Not enough video memory.  Disabling DRI.
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0
lines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
               large DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
               small DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(WW) intel(0): Not enough video memory.  Disabling DRI.
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0

---

### Post by sciurus on 2007-07-29
What driver was it using when you received it?

---

### Post by Junkhead on 2007-07-29
Try the command: sudo modprobe agpgart

 before you start X with the intel driver.

---

