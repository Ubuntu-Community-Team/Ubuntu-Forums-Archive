---
title: "High CPU utilization by systemd-udevd"
date: 2019-07-31
forum: Desktop Environments
---

### Post by gdesilva on 2019-07-31
Hi, I am running Ubuntu Studio 10.04 5.0.0-21-lowlatency and have had some issues which appears to be related to the use of Dell USB Bluetooth adaptor.

Upon checking I found out that systemd-udevd sometime consumes over 40% cpu. I have tried various solutions outlined in other forums including stopping and starting systemd-udevd. I noticed that the cpu utilization slowly creeps up after a while.

Would appreciate if anyone has any suggestions.

Thanks

---

### Post by jeremy31 on 2019-07-31
Anything show in dmesg log?  There might be a udev rule running in a loop

---

### Post by gdesilva on 2019-07-31
@jeremy31, thanks for the response. I did a udevadm monitor and get the following output which appears to be what you suggested. How do I isolate the offending device? I guess I could just not use the BT adaptor but is there a fix for this? Thanks.

```

$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[8014.820106] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8014.944086] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
KERNEL[8015.028121] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
UDEV  [8015.028557] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8015.236066] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8015.264019] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
KERNEL[8015.444065] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8015.584147] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
UDEV  [8015.584458] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
KERNEL[8015.652086] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8015.860053] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8015.904054] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
KERNEL[8016.068046] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8016.224072] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
KERNEL[8016.276119] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
UDEV  [8016.276569] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8016.484054] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb3/3-0:1.0 (usb)
KERNEL[8016.545061] change   /devices/pci0000:00/0000:00:1c.4/0000:03:00.0/usb4/4-0:1.0 (usb)
```

---

### Post by Autodave on 2019-07-31
10.4?  Really?  That was dead years ago.

---

### Post by gdesilva on 2019-07-31
Sorry, 19.04 - a typo!

---

### Post by jeremy31 on 2019-07-31
Post results for ```
lsusb
```

---

### Post by gdesilva on 2019-07-31
$ lsusb
Bus 002 Device 004: ID 0480:b207 Toshiba America Inc Canvio Ready
Bus 002 Device 006: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 002 Device 005: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 002 Device 007: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 002 Device 003: ID 046d:0b02 Logitech, Inc. C-UV35 [Bluetooth Mini-Receiver] (HID proxy mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2019-07-31
Edit the file /lib/udev/rules.d/97-hid2hci.rules
and comment out

```
# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[3bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```

Then reboot and see if the bluetooth still works.  If that doesn't work change line 3 of that file as described in [https://bugzilla.kernel.org/show_bug.cgi?id=199035#c4](https://bugzilla.kernel.org/show_bug.cgi?id=199035#c4)

---

### Post by gdesilva on 2019-07-31
@jeremy31 - thanks for your suggestion. 

However, before I saw your post, I did some tweaks in the /etc/bluetooth/main.conf file - namely, set PairableTimeout = 0 and FastConnectable = true and rebooted and now udevadm monitor does not scroll on with messages and systemd-udevd does not appear at all on the active processes. The reason why I was prompted to set PairableTimeout to 0 was because my bluetooth devices would constantly drop the connection when left to idle for a while which was annoying to say the least. Similar reasoning to set FastConnectable to true as to get the connection re-established after idle I would have to press a few keys to activate the connection - I guess this will increase the power consumption on the devices but it does not drive me crazy!!

I will monitor the situation for a while and if the problem recurs will try out your suggestion.

Many thanks for your help.

---

### Post by gdesilva on 2019-08-01
Strange.....this morning as I mentioned I thought I had fixed the problem. For over 2 hours the system ran without any udev messages and I did not notice any systemd-udevd processes running.

However, just now restarted the system and I am back at square one! Tried commenting out Logitech devices in 97-hid2hci.rules but it made no difference. Tried after removing 97-hid2hci.rules as suggested in one post [https://askubuntu.com/questions/1028883/ubuntu-18-04-systemd-udevd-uses-high-cpu-conflict-with-wifi](https://askubuntu.com/questions/1028883/ubuntu-18-04-systemd-udevd-uses-high-cpu-conflict-with-wifi) but still no success.

EDIT: did not do any upgrades or system modifications since this morning either....

---

### Post by gdesilva on 2019-08-01
Tried the following;

1. Removed the bluetooth dongle and the devices and used a PS2 keyboard and a USB mouse. udevadm monitor scrolls with a list of messages. systemd-udevd gets up to around 7% cpu (in about 10 minutes)

2. booted using 5.0.0.20-lowlatency (the previous kernel) but no change in udevadm monitor.

From above it appears that the issue is unrelated to bluetooth as I am now not running any bluetooth devices or dongles but related to USB??

---

### Post by gdesilva on 2019-08-01
OK - fixed it!

The problem as I mentioned in one of the earlier posts had nothing to do with the bluetooth adapter or devices but related to a USB3 card I had installed some time ago.

I noticed that the power cable to the USB3 card was not connected properly. All I had to do was to re-seat power cable and all the messages from udevadm monitor went off. 

Thanks everyone for the suggestions.

---

