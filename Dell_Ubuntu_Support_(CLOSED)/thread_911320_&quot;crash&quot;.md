---
title: "&quot;crash&quot;"
date: 2008-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denny Johnson on 2008-09-05
I've a 1420n, about a week ago upgraded to 7.10 and then 8.04.
Everything pretty much OK ex some standby issues.
This morning I downloaded a new batch of upgrades, about 48 of them IIRC, mostly language related, but a few non language at the end.
I've tried to reboot several times since, every time:
- the Dell page
- a brief "Grub" screen
- the Ubuntu page, the Orange line gets only about 20% across and then
- a blank screen w a flashing dash in the upper left hand corner.

As you can probably tell by how I've expressed myself here, I'm not a techie.
Could someone please tell or point me to info re how to proceed from here......I reckon I want to get my computer working so that I can remove today's upgrades.
Any knowledgeable suggestions appreciated.
Thanks

---

### Post by prshah on 2008-09-05
> **Denny Johnson said:**
> 
I've tried to reboot several times since, every time:
- a blank screen w a flashing dash in the upper left hand corner.


How long have you actually waited at the blank screen? Is there any HDD activity during this period?

In any case, can you load a virtual terminal? (Press Ctrl+Alt+F1). If that shows up, login, and give the command ```
startx
```. If it works, you should have GUI, but if it doesn't (and I suspect it won't), post back the error message(s) that it spits out.

Often, the last error message as not as helpful as the earlier messages, so post everything it gives you after the above command. (Maybe about 5-15 lines).

Please also post the output to the commands ```
dmesg | tail
tail /var/log/Xorg.0.log
```

---

### Post by Denny Johnson on 2008-09-05
Thanks prshah,
It seems to have fixed itself.
When I had the problem, sometimes I waited on the blank screen for several minutes.
I'm assuming that HDD means hard drive, I don't know if there was activity.
At one point I did Press Ctrl+Alt+F1, no response, tho I probably didn't give it much time.
Current output to the commands:
```
denjohn@dell:~$ dmesg | tail
[   81.204000] input: Logitech USB Receiver as /class/input/input9
[   81.204000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   81.208000] usbcore: registered new interface driver usbhid
[   81.208000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   81.524000] NET: Registered protocol family 17
[   82.192000] usbcore: registered new interface driver xpad
[   82.192000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   85.128000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   95.864000] eth1: no IPv6 routers present
[  111.924000] eth1: no IPv6 routers present
denjohn@dell:~$ tail /var/log/Xorg.0.log
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "CMO", prod id 5158
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.40  1280 1328 1360 1445  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID vendor "CMO", prod id 5158
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
denjohn@dell:~$ 


```

---

