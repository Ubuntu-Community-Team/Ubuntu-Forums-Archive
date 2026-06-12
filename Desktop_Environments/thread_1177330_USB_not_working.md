---
title: "USB not working"
date: 2009-06-03
forum: Desktop Environments
---

### Post by mattylaws on 2009-06-03
Hi all.

I recently built a computer using an Intel Celeron D865GLC motherboard and a 2.8Ghz CPU. 

I managed to boot puppy linux from a live cd and the keyboard and mouse worked fine (both were USB) but when I installed it onto the hard drive both failed to function, forcing me to find and use an old PS/2 keyboard (which I actually prefer). So now I decided I wanted to be gui-less, and using ubuntu alternate installer I installed a basic package, but usb still doesn't work (after attempting to use a wireless receiver and memory stick). I've tried apci=off and noapic to no avail (though I have a very basic knowledge of what they do). Whenever I plug a USB device in it comes up with error messages like "Failed to allocate device". This always seems to happen when I install it onto HD, but when it's booted from a live CD it works fine. 

So I can only assume something went wrong in the installation, but I'm no Linux veteran so have no idea where to start fixing it.

Thanks for any help

Matt

---

### Post by mmarif4u on 2009-06-03
Now you are referring to USB flash and external HDD drives OR mouse and keyboard.

---

### Post by mattylaws on 2009-06-05
Both, no USB devices seem to be working

---

### Post by Jonnox on 2009-06-05
Possibly a permissions issue. try ```
lsusb
``` to ensure that your kernel is recognizing your USB stick, then try ```
sudo mount /dev/disk/by-id/<usb entry> /media
``` and see if it still gives you the error

---

### Post by us marraige on 2009-06-06
I'm using Windows XP SP2. Heres my problem. My usb ports suddenly stopped working. i had not installed any new programs, just one day i went plugged in my ipod, it charged perfectly but my PC did not know anything was there. Same thing with my printer, when i turn it on PC doenst know anything is there. i've tried uninsalling the usb drivers in device manager and reinstalling, but that didn't work.

If anyone has any way to figure out what's wrong with them other than formating and reinstalling windows.

thanks

---

