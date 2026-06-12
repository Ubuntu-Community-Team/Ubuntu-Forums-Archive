---
title: "Virtual Box error with usb"
date: 2009-02-22
forum: General Help
---

### Post by Jacopomsn on 2009-02-22
hi everyone in the internet, i would like to ask you a possible solution for one big problem that i have...

```

No hard disk attached to device slot 0 on channel 1 of bus 1.


Codice&nbspd'uscita: 
VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
Componente: 
Machine
Interfaccia: 
IMachine {ea6fb7ea-1993-4642-b113-f29eb39e0df0}


USB device 'Logitech USB-PS/2 Optical Mouse' with UUID {c311bd6c-f342-4a10-9846-071d0721be1a} is busy with a previous request. Please try again later.


Codice&nbspd'uscita: 
NS_ERROR_INVALID_ARG (0x80070057)
Componente: 
HostUSBDevice
Interfaccia: 
IHostUSBDevice {173b4b44-d268-4334-a00d-b6521c9a740a}
Chiamante: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

```


Other times give me this error
```


USB device 'Logitech USB-PS/2 Optical Mouse' with UUID {c311bd6c-f342-4a10-9846-071d0721be1a} is busy with a previous request. Please try again later.


Codice&nbspd'uscita: 
NS_ERROR_INVALID_ARG (0x80070057)
Componente: 
HostUSBDevice
Interfaccia: 
IHostUSBDevice {173b4b44-d268-4334-a00d-b6521c9a740a}
Chiamante: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

```


Thanks a lot and sorry for my english, i'm italian:D

---

### Post by ubu-for on 2009-03-22
I have the same problems with Win XP Home and Win 7 Beta as guest OS and the following tips didn't solve my USB problem. Maybe you have more luck.

[http://ubuntuforums.org/showpost.php?p=2366065&postcount=72](http://ubuntuforums.org/showpost.php?p=2366065&postcount=72)

I'm using Ubuntu 9.04 Alpha 6 and Sun Microsystem's VirtualBox 2.1.4 (Intrepid Ibex) with USB support, so I don't have a problem with the USB mouse and keyboard but with my USB hard disk and memory stick.

Does anybody else have some further tips to solve the USB problem?

Thanks in advance!

P.S. I also had no success with the [option to share folders](http://forums.virtualbox.org/viewtopic.php?p=33944#p33945) between the host and guest OS.

---

### Post by conryf on 2009-03-22
Hi All,

 I just solved my usb mouse problem on a hunch. I had enabled usb 2.0 and selected a filter for my USB mouse. Oddly what fixed it was for me to delete the filter for my USB Mouse device and now it works like a charm.

I wasn't aable to get my evternal or mamory stick working but I did get shared folders. What's the exact trouble ubu-for? Did you install guest additions?

Hope this helps!

---

### Post by ubu-for on 2009-03-23
> **conryf said:**
> I wasn't aable to get my evternal or mamory stick working but I did get shared folders. What's the exact trouble ubu-for? Did you install guest additions?
Yes, I did but I didn't try both at the same time. ;)

Now if I enter the following code in Windows a window pops up for a few seconds and I get my shared folder.

```
net use E: \\vboxsvr\Share
```

[http://forums.virtualbox.org/viewtopic.php?p=33944#p33945](http://forums.virtualbox.org/viewtopic.php?p=33944#p33945)

Thank you so much! :D

---

