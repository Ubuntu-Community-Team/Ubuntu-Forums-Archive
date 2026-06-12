---
title: "Serial Port -&gt; USB Conversion"
date: 2012-09-21
forum: Desktop Environments
---

### Post by Martyn Thompson on 2012-09-21
Hi everyone,

I am using a Windows only piece of software called Suunto Dive Manager and running it through Wine (standard Ubuntu install of Wine). 

The problem I have is that I am running this on my laptop which doesn't have any serial ports.  The hardware connection is serial but I am using a cable converter so I can fit connect to the USB ports on the laptop.  This seems to work well and looking at dmesg|tail reveals:
```

[  415.752177] usb 3-2: new full-speed USB device number 3 using ohci_hcd
[  415.920579] pl2303 3-2:1.0: pl2303 converter detected
[  415.942821] usb 3-2: pl2303 converter now attached to ttyUSB0

```

The Suunto Dive Manager expects to read from a COM port.  

So, the question I have is, is there a way in which I can forward the USB0 to a COM port and if so, how do I do it?  

Alternatively, am I barking up the wrong tree and has anyone got other advice?

---

### Post by drdos2006 on 2012-09-21
Check this out.

[http://www.lvr.com/usb_virtual_com_port.htm](http://www.lvr.com/usb_virtual_com_port.htm)
[quote]
The important information is :
COM ports have long provided a convenient way for PCs and embedded systems to exchange information. The traditional COM port on a PC is an RS-232 serial port on a motherboard or expansion card. Recent PCs often skip RS-232 in favor of USB. But with the right firmware, a USB device can appear as a virtual COM port that applications can access using .NET's SerialPort class or other COM-port APIs or libraries.
[\quote]

You might find it easier to access a box with a serial port rather than having to add firmaware.

regards

---

### Post by Martyn Thompson on 2012-09-22
Cheers for that DrDos.  I wondered if that might be the case.

I do have a full sized desktop system upstairs so will need to use that I reckon.

Thanks for the advice.

---

