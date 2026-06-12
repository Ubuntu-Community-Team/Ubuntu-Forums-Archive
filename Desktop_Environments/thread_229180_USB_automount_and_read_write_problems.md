---
title: "USB automount and read write problems"
date: 2006-08-04
forum: Desktop Environments
---

### Post by shrift on 2006-08-04
I see this issue all over the forums, and I have also been bitten to it, and I can't seem to find an answer. The issue is this; when you plug in a usb device it gets automounted by dapper. Dapper mounts it however it sees fit. And as far as I can tell there is no way to edit how dapper manages the automount! Example:
If I were to plug in a fat32 formatted usb device, dapper would mount it without proper read/write functions. IE: the umask=077 does not allow me to write properly.

And please do NOT tell me to use the fstab. I have several USB devices that I plugin, and I do not want to have to tell them to mount manually everytime they plugin, AND they don't receive a predictable device name, due to them being USB devices.

If anyone can tell me where to change the options that Dapper uses for automounting, that would be awesome.

Thanks for looking at this.

---

### Post by ajgreeny on 2006-08-04
This is something that would be very useful to me as well.  It would save having to write to the usb flash drive as root, which just adds to the nuisance value.  Surely it should be dead simple to write to flash drives without having to bother about this palaver, then I could simply drag and drop the files I want to the drive without having to use konqueror as root, something I try to avoid if possible.

Please don't suggest using the command line, as it means, for example, that when I want to sort out some, but not all, photos from a folder to put on the flash drive there is no simple way (that I know of) of doing it by terminal commands without copying the name of each photo, or I suppose temporarily moving the photos I don't want to copy over.  Surely just easier to drag and drop.

---

### Post by shrift on 2006-08-07
So nobody knows how this works? If not I am going to open a bug for this. Please help me someone!

---

### Post by duan on 2006-08-07
mounting hot-swappable bitties reliably is handled by HAL/udev in ubuntu.
Basically what the HAL/udev system does is it reads the proprietary info of any hotswap device and matches it against some preset parameters and then remebers what to do with it. 

If you find your distro handles the same device differently and it annoys you then you can add an entry to udev for it. 

With this you can do a lot more: you can determine by serial number, size, vendor name e.t.c and there are some unique identifiers to every device so every device you have can be handled uniquely. 

You can then determine which users can/cannot use the device, or at the very least how it is mounted, (and then add it to /etc/fstab so that your reqular users can mount it)

I haven't needed to do that yet since my usb device was formated with a volume label and it is always mounted as /media/<VOLUME_LABEL>

Have a search through the forums or the web for udev.

---

