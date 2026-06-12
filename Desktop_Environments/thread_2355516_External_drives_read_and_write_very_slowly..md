---
title: "External drives read and write very slowly."
date: 2017-03-13
forum: Desktop Environments
---

### Post by tashimee2 on 2017-03-13
I just bought a new motherboard (Asus b150-plus), running dual boot ubuntu 16.04 and win7. Everything works fine in windows, but Ubuntu has a problem with the usb ports. It won't recognize the usb 3.0 ports at all, and the usb 2.0 ports run at about 600 kB/sec. It takes days to backup one of my hard disks. Is there anything I can do about this. I have been looking around the web for answers and can't really find any info.

I would appreciate any help.

---

### Post by TheFu on 2017-03-13
You can check the USB chips used and see if there are any known fixes for those specific chips.  **lshw** and **lsusb** will be helpful.  

BTW, on one of my older systems USB3 performance is terrible because the motherboard wasn't designed for all that throughput, but on a newer box ($45 motherboard), USB3 performance is totally fantastic.

---

### Post by tashimee2 on 2017-03-13
tashimee@tashimee:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 059f:1018 LaCie, Ltd Desktop Hard Drive
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 059f:1018 LaCie, Ltd Desktop Hard Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Go to [https://paste.ubuntu.com/24173665/](https://paste.ubuntu.com/24173665/) for lshw.

---

### Post by TheFu on 2017-03-13
If you use **lsusb -t**, you'll see how things are connected.  It appears the devices are connected to a USB2 port, if I'm reading the **lshw** output correctly.  Is that what you see?

Nothing appears to be connected to the USB3 controller.

You can check the manpages for those commands for more interesting options. That is always useful.

---

### Post by tashimee2 on 2017-03-13
I updated the bios (several people suggested that) but it doesn't seem to make any difference.

Then why does it work in windows?


tashimee@tashimee:~$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 8: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 8: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 8: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 9: Dev 6, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 10: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 480M


Would plugging in a usb card help?

I tried usbview and got this error message:
Can not open the file /sys/kernel/debug/usb/devices

 Verify that you have USB compiled into your kernel, 
 have the USB core modules loaded, and have the 
 usbdevfs filesystem mounted.

---

### Post by TheFu on 2017-03-14
Bus 1 is USB2 only. 480Mbps.

You need to plug the disks into Bus 2 which supports the higher speeds - 5Gbps.

If you plug the drives into the wrong ports, a usb addon card won't help. I've never heard of usbview. sorry.

---

### Post by tashimee2 on 2017-03-15
So how do I get to bus 2?

And why is bus 1 running at such a slow speed?

---

### Post by TheFu on 2017-03-15
> **tashimee2 said:**
> So how do I get to bus 2?

And why is bus 1 running at such a slow speed?

Bus to is connected to different external USB ports. Try the other ports!

Bus 1 is USB2/USB1.1 and USB1.0. It can't go any faster than 480Mbps - about 60 MBps - that's a theoretical limitation, but real world USB2 is about 1/3rd of that, sometimes less. This is shared by all the devices on the same bus.

---

### Post by tashimee2 on 2017-03-15
If I plug my usb 3.0 drive into the 3.0 port Ubuntu doesn't recognize that it is there. It I plug it into a 2.0 port it works fine at the same speed as a 2.0 drive.
The usb 2.0 ports are running at about 600 KBps. It is like I need to add an extra driver or something. I'm beginning to think that Ubuntu won't work on the new motherboards. I do not want to go back to using the windows.

---

### Post by TheFu on 2017-03-15
I did the google search for the USB3 bus you have.
[https://askubuntu.com/questions/210879/external-usb-3-drive-not-recognized](https://askubuntu.com/questions/210879/external-usb-3-drive-not-recognized) says, 

> The USB 3.0 device is not providing latency info.

When you connect a USB device the kernel provides a 10ms delay for the device to initialize, then the kernel begins sending commands to the device.

The delay is hard coded into the kernel for USB2.0 devices, but for 3.0 devices the value is configurable and is provided by the device.

If the device does not provide the latency value for the kernel, the kernel will never send commands to the drive because it will wait forever.

The only way to fix this is to either get a different drive enclosure (yours is broken) or patch the kernel to use the default latency in USB3.0, which would be very difficult and possibly also break other things.

There have been a number of USB3 issues. Here's one with some tips that may or may not be helpful.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242321)

As for the lower speed on the USB2 connections - some USB2 ports don't provide sufficient power. Are your drives externally powered?

I'd try a different distro - perhaps straight debian and/or SUSE to see if that solves it too (both USB3 and slow USB2 access).  Ubuntu derivatives probably won't help. 

That's all I got.

---

### Post by tashimee2 on 2017-03-16
Thank you for your help. It doesn't solve the problem, but it gives me a place to start.

---

