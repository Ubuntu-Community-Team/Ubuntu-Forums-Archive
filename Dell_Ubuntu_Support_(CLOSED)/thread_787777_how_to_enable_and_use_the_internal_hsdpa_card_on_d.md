---
title: "how to enable and use the internal hsdpa card on dell d630"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by msvalente24 on 2008-05-09
I searched everywhere on the net and didnt find any info, managed to figure it out myself. Therefore since i couldn't find anything i decided to share my experience in the hopes of helping someone else out.

this what I did on my dell d630
download and install the betavine vodafone driver for linux

then in the terminal

"sudo lsusb -v | less"

look at the devices, its a long list scroll down till you find the internal card, Mine looks like this:
Bus 002 Device 003: ID 413c:8137 Dell Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8137 
  bcdDevice            0.00
  iManufacturer           1 Novatel Wireless
  iProduct                2 Novatel Wireless HSDPA Modem
  iSerial                 2 Novatel Wireless HSDPA Modem
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9


then once you have done that take note of the id vendor and id product value.

thne type in the terminal

"sudo modprobe usbserial vendor=0x413c product=0x8115" (insert your own idproduct and idvendor number in the vendor and product fields that you previously took note of)

then

"grep tty /var/log/messages" and check to see if the output says the modem is attatched to ttyUSB1 0r ttyUSB0

now launch the vodafone driver for linux

when presented with the device set up, choose serial in the drop down list and in the two entry fields typt ttyUSB0 or ttyUSB1 depending on where the modem is attatched ie look at the "grep tty /var/log/messages" output.

I hope some1 found this valuable and i saved someone hours of frustration

Peace out!



one more thing to make sure the devices is activated at boot:
"sudo gedit /etc/modules"
add to the end of file  "echo usbserial vendor=0x4XXX product=0x81XX"  (X = your specifiv vendor and prouct ID)

---

### Post by sbrbot on 2009-01-21
I've got the same Dell D630 with the same HSDPA built-in GSM card and my "grep tty /var/log/messages" gives this output:

```
Jan 20 18:33:11 CyberBlade kernel: [    0.004000] console [tty0] enabled
Jan 20 18:33:11 CyberBlade kernel: [    1.701516] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 20 18:33:11 CyberBlade kernel: [    1.702087] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 20 18:33:11 CyberBlade kernel: [   16.644247] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
Jan 20 18:33:11 CyberBlade kernel: [   16.644314] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
Jan 20 18:36:37 CyberBlade kernel: [  226.822900] type=1503 audit(1232472997.288:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=6766 profile="/usr/sbin/cupsd"
Jan 20 18:36:37 CyberBlade kernel: [  226.825642] type=1503 audit(1232472997.292:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=6766 profile="/usr/sbin/cupsd"
Jan 20 20:04:57 CyberBlade kernel: [    0.004000] console [tty0] enabled
Jan 20 20:04:57 CyberBlade kernel: [    1.705186] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 20 20:04:57 CyberBlade kernel: [    1.705755] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 20 20:04:57 CyberBlade kernel: [   16.697650] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Jan 20 20:04:57 CyberBlade kernel: [   16.697715] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Jan 20 20:06:51 CyberBlade kernel: [  135.923813] type=1503 audit(1232478411.585:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=6738 profile="/usr/sbin/cupsd"
Jan 20 20:06:51 CyberBlade kernel: [  135.926701] type=1503 audit(1232478411.590:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=6738 profile="/usr/sbin/cupsd"
Jan 21 17:23:55 CyberBlade kernel: [    0.004000] console [tty0] enabled
Jan 21 17:23:55 CyberBlade kernel: [    1.705656] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 21 17:23:55 CyberBlade kernel: [    1.706224] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 21 17:23:55 CyberBlade kernel: [   16.881655] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Jan 21 17:23:55 CyberBlade kernel: [   16.881718] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Jan 21 17:29:04 CyberBlade kernel: [  331.042929] type=1503 audit(1232555344.722:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=6774 profile="/usr/sbin/cupsd"
Jan 21 17:29:04 CyberBlade kernel: [  331.042976] type=1503 audit(1232555344.722:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=6774 profile="/usr/sbin/cupsd"

```

And Vodaphone Mobile Connect Card driver cannot find my card.

---

### Post by stoyac on 2011-01-01
Dell Latitude D630, OpenSuSE 11.3, uname -a:
```

Linux daniel 2.6.34-12-desktop #1 SMP PREEMPT 2010-06-29 02:39:08 +0200 x86_64 x86_64 x86_64 GNU/Linux

```my lsusb output:
```

Bus 004 Device 002: ID 413c:8137 Dell Computer Corp. Wireless 5520 Voda L Mobile Broadband (3G HSDPA) Minicard Status Port

```The kernel module usbserial makes this modem available as ttyUSB0 or ttyUSB1, dmesg:
```

usbserial: USB Serial Driver core
USB Serial support registered for GSM modem (1-port)
option 4-2:1.0: GSM modem (1-port) converter detected
usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
option 4-2:1.1: GSM modem (1-port) converter detected
usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
usbcore: registered new interface driver option
option: v0.7.2:USB Driver for GSM modems

```The modem can be used by simply putting the SIM card into the slot behind the battery of the notebook and using wvdial for initializing the SIM card with the PIN and making a connection to the provider. Here my /etc/wvdial.conf for connecting with the German provider FYVE (D2 Vodafone):

```

[Dialer Defaults]
Init1 = AT
Init2 = ATV1 E1 S0=0 &C1 &D2
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0

[Dialer umts-pin]
Init3 = AT+CPIN=1234

[Dialer umts]
Dial Command = ATD
Carrier Check = no
Phone = *99***1#
Password = notneeded
Username = notneeded
Stupid mode = 1
Init4 = AT+CGDCONT=1,&quot;IP&quot;,&quot;web.vodafone.de&quot;

```The SIM card has to be initialized once after booting using ''wvdial umts-pin'' and connection is made using ''wvdial umts''. Under circumstance you'll have to call wvdial as root or using sudo.

Best thanks to kampmann on [http://www.linuxforums.org/forum/wireless-internet/125558-3g-umts-problem-creating-connection-wvdial.html](http://www.linuxforums.org/forum/wireless-internet/125558-3g-umts-problem-creating-connection-wvdial.html) for this good hint.

Don't also forget to activate the modem using the switch on the left of D630, the same switch as used for Bluetooth or wireless. Be also aware, that the UMTS modem doesn't seem to understand few AT commands like ATZ or ATQ0, used in every example or defaults for wvdial.

---

### Post by kalamaster on 2011-05-13
Hi stoyac,
did you know if is possible to connect to other apn using wdialconf method (for example h3g (Three) for Italy)
thanks a lot
K

---

