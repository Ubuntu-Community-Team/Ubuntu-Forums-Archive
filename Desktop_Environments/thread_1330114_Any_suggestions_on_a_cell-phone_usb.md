---
title: "Any suggestions on a cell-phone usb?"
date: 2009-11-18
forum: Desktop Environments
---

### Post by MetroidJunkie2008 on 2009-11-18
I have a cellphone with micro sd storage and with a usb cable. When I connect it, it goes into File Transfer Mode but no drive appears on Ubuntu. Shouldn't it treat it like regular usb storage?


Just as a side-note, I have Ubuntu 9.10

---

### Post by emigrant on 2009-11-18
Iv a SE k530 and when i plug in it asks me which mode i want to select. Filetransfer/phone mode.

Whats ur make?

---

### Post by MetroidJunkie2008 on 2009-11-18
It's a Kyocera Slider Sonic by Virgin Mobile, it goes to file transfer mode automatically when it's connected, which it did, and it would normally be treated like a usb connection, with the micro sd contents appearing as a drive. The phone's in file transfer but the drive isn't showing.

---

### Post by iris-n on 2009-11-18
Hi Metroid.

I think I can help you.

Does the cell phone appears when you type lsusb?

If so, try ```
sudo mv /lib/udev/rules.d/60-persistent-storages.rules /lib/udev
```

That's just to stop the faulty command being executed. Then ```
ls /dev/sd*
```, plug in the phone, ```
ls /dev/sd*
```, to see whether it was detected.

If it was, you can mount it manually now. If it wasn't, sorry, I can't help you.

If this is the problem, I can make it automount too.
Just remember to move the file back to where it belongs if you want your computer to boot.

---

### Post by crogers on 2013-01-24
> **emigrant said:**
> Iv a SE k530 and when i plug in it asks me which mode i want to select. Filetransfer/phone mode.

Whats ur make?
You've been waiting a long time for no answer! Kinda makes one wonder what's the use, eh?
I found this "thread" in Jan, 2013 when I started looking for an answer to a similar problem with my Z431 phone. I have a Windows machine that works OK with the Bluetooth dongle and the USB cable.  So that's the solution to my interface, issue. But, I'd love to fire Microsoft and use only Ubuntu. 

Unfortunately,  I have tried both Bluetooth and USB using both a desktop Ubuntu and  an Acer netbook Ubuntu. Neither one could "pair" with the phone using Bluetooth. Both thought the phone was an unformatted CD when connected with USB. I conclude that Ubuntu doesn't work with my phone. (It's things like this that make me keep an old Windows machine around.)

:mad:
Anybody want to correct my thinking on this?
):P

---

