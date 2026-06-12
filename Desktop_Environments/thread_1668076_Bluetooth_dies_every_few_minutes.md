---
title: "Bluetooth dies every few minutes"
date: 2011-01-15
forum: Desktop Environments
---

### Post by InnerBushman on 2011-01-15
Hi.
My bluetooth manager is dying every few minutes or even every few couple of seconds.
This happens when i'm using bluetooth mouse. Mouse works correctly cause i've tested it in windows. In the attachment there is dmesg output. In dmesg i keep geting lines like:
> [ 1463.864082] usb 4-1: USB disconnect, address 10
[ 1463.864601] btusb_intr_complete: hci0 urb eddf2900 failed to resubmit (19)
followed by reconnecting both, USB dongle and mouse. Then it works for a while and dies again, over and over.
It also happens when mouse it idle (no matter if 5 seconds or 5 minutes).

How to fix it? Any ideas what could that be?

Thanks in advance,
Bushman

attachment: dmesg > [http://bushman.pastebin.com/Uq3CiY3c](http://bushman.pastebin.com/Uq3CiY3c)

PS: i can provide any other info on request in order to help solving the problem

---

### Post by InnerBushman on 2011-01-24
I've posted a bug report on LKML
[https://lkml.org/lkml/2011/1/19/168](https://lkml.org/lkml/2011/1/19/168)

Still no luck solving it. Anyone?!

---

### Post by dileepm on 2011-01-27
Have you somehow enabled an temporary bluetooth connection to stay up for some 10 mins or so?

---

### Post by InnerBushman on 2011-01-28
No, i haven't enabled any bluetooth timers. It happens in **random** intervals. Some times 10 seconds, some times 5 minutes.

---

### Post by InnerBushman on 2011-02-04
> **dileepm said:**
> Have you somehow enabled an temporary bluetooth connection to stay up for some 10 mins or so?

Where can i find such timers? (except "temporary visible" wich is by default on and not in action when working with the mouse)

---

### Post by InnerBushman on 2011-02-13
i've checked my mouse on other BT dongle device (the BT chip is of the same manufacturer, different model). it works flawlesly. then again i've checked the faulty BT dongle in virtualised windows XP on the same machine and it works flawlesly too. same USB port, same mouse, same dongle, diferent driver. it must be something in USB or bluetooth driver of linux. would be nice if someone would help me find the reason of the bug. the bug itself is quite visible as is without actualy looking for it.

---

### Post by insert_name_here on 2011-03-08
I believe I've got the same problem as InnerBushman.

I pair my mouse with my internal bluetooth. The mouse functions fine for a while, then randomly stops working. I have to remove the device from Ubuntu's bluetooth manager, then Set Up New Device again.

dmesg output: 

```
[523450.545100] usb 5-1: USB disconnect, address 14
[523450.545265] btusb_intr_complete: hci0 urb f2ca7180 failed to resubmit (19)
[523450.545288] btusb_bulk_complete: hci0 urb f2ca7880 failed to resubmit (19)
[523450.546272] btusb_bulk_complete: hci0 urb ef852f00 failed to resubmit (19)
[523450.546770] btusb_send_frame: hci0 urb f2e08800 submission failed
```

Mouse model is Microsoft Wireless Notebook Presenter Mouse 8000. Internal bluetooth is [Broadcom Thinkpad Bluetooth]("http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_(BDC-2)") in a Lenovo T60 on 10.04.

---

