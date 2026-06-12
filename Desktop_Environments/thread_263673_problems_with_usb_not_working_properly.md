---
title: "problems with usb not working properly"
date: 2006-09-23
forum: Desktop Environments
---

### Post by kroywen on 2006-09-23
Hi,
i have problem with usb (as in the title). I have a digital camera, that I have plugged in several times and it was working properly. But few days ago i've wanted to use usb pendrive and when i've plugged it in nothing happened. From that moment on no matter what I plug into one of 4 usb ports on my computer, nothing happens. I've googled some forums for this problem but no one seems to be having the same problem. I'm working on Intel 845GVM motherboard (celeron 2,4 GHz, 768 RAM) with Drapper installed. Frankly I don't know what to do or where to search for error, but I can post some outputs here.
(It was done with pendrive plugged in)

lsusb:

Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

lspci | grep USB

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)

dmesg | grep USB usb

[4294676.600000] usbcore: registered new driver usbfs
[4294676.600000] usbcore: registered new driver hub
[4294671.819000] SLPB PCI0 HUB0 USB0 USB1 USB2 USBE
[4294676.602000] USB Universal Host Controller Interface driver v2.3
[4294676.603000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.604000] hub 1-0:1.0: USB hub found
[4294676.705000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.705000] hub 2-0:1.0: USB hub found
[4294676.806000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294676.806000] hub 3-0:1.0: USB hub found
[4294676.910000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294676.914000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.914000] hub 4-0:1.0: USB hub found

if any other information is needed just ask

---

### Post by kroywen on 2006-09-24
Really anybody hasn't got any idea?

---

### Post by Deka on 2006-09-30
I seem to be having the same issue. I just installed a few hours ago. drapper-desktop 6.06.1


```
drew@drew-desktop:~$ cat /proc/version
Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
```

---

### Post by Deka on 2006-09-30
Its weird.. when I plug something in USB nothing happens at all. I know its not a hardware issue.

I did "tail -f /var/log/messages" and plugged something in a memory stick.. nothing changed. I then plugged in an external drive.. nothing. I tried different ports too. Also, lsusb doesnt list anything.

---

### Post by lonelypauly on 2006-09-30
i know this sounds silly, but did you try rebooting?

---

### Post by Deka on 2006-09-30
Yes

---

### Post by Deka on 2006-10-01
nobody? :/

could it be the kernel? apparently 2.6.x has some usb issues? (another thread)


drew@drew-desktop:~$ uname -r
2.6.15-27-386

---

### Post by Deka on 2006-10-03
Heh... it was my fault. :(

I had an issue the other day and set my bios to fail-safe defaults, which disables usb controllers. Just had to enable all... [-( ](*,)

---

