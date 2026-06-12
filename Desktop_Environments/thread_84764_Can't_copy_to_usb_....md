---
title: "Can't copy to usb ..."
date: 2005-10-31
forum: Desktop Environments
---

### Post by dbee on 2005-10-31
When I try to copy files to my usb drive, I get just the directory structure on the usb drive but the files themselves don't copy.

It seems like the copy progress bar gets to about half-way and then just disappears... :( 

I can copy the files in one at a time no problem though.

---

### Post by dbott67 on 2005-10-31
Does this happen when using Nautilus and when using the cp command from a terminal?  Try copying a directory from your hard drive to your USB drive using the cp command and see what happens.

-Dave

---

### Post by Polmac on 2005-11-02
I'm having a similar problem, and it also happens using the cp command. 

I'll explain what happens: I copy a folder full of mp3 songs (80 mb, let's say) to my usb (122 mb), and the system does it veeery fast. When I open them, the first songs are usually ok, but the rest of them only sound for a few seconds, or nothing at all.

Then the system claims that the usb device has only 42 mb left, as if it had fully copied the songs. When I delete them, it  claims the device to have only about 60 mb of free space (instead of 122) and I have to format it to "recover" the rest of my memory size. (Yes, I had also removed the .trash folder, and 62 mb where "lost")

It's weird and disturbing...

Anyone can help?

---

### Post by Quirky on 2005-11-06
It's probably a bug. See here for some details [http://bugzilla.ubuntu.com/show_bug.cgi?id=13169](http://bugzilla.ubuntu.com/show_bug.cgi?id=13169)

What's happening is that the copy is buffered and doesn't really copy until you unmount the device, flushing the buffer. The safe way to copy is copy your files as usual, then open a terminal and type **pumount */media/usbdevice*** replacing /media/usbdevice with the correct mount point for your MP3 player. *This operation will block until the copy buffer has been flushed and the device unmounted.* Now you can unplug your USB device.

Alternatively, unmount the device by right clicking its icon on the desktop and wait until your MP3 player stops showing a 'copying' icon on its display (if it has one) or until your CPU level doesn't show a high usage %; this indicates it is still copying the files. Use System Tools->System Monitor to see CPU level.

It is, I think you'll agree, not very user friendly. But at least all your songs are copied correctly if you use this paranoid approach.

---

### Post by simplyw00x on 2005-11-06
The simple problem is that if you delete anything on a USB drive it instead moves it to a hidden trash folder on that drive. Try pressing Ctrl+H in nautilus whilst in the USB drive and deleting the .User_Trash folder.

---

