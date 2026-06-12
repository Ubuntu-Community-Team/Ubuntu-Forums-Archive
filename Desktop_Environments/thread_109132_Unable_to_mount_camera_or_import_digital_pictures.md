---
title: "Unable to mount camera or import digital pictures"
date: 2005-12-27
forum: Desktop Environments
---

### Post by jdway on 2005-12-27
I am having problems importing pictures from my HP Photosmart E317. There are pictures stored on the camera but when I plug the camera into the usb drive it reads the camera as a USB PTP class camera but it will not detect the pictures that are stored on the camera. I have both gthumb and gkam installed but neither will read the camera. I also read on other threads in the forum that when you plug the camera into the usb drive an icon should appear on the desktop but it does not. I looked on the computer and file system but I could not find the camera listed anywhere.

---

### Post by stuporglue on 2005-12-27
> I also read on other threads in the forum that when you plug the camera into the usb drive an icon should appear on the desktop but it does not. I looked on the computer and file system but I could not find the camera listed anywhere.

If you're using PTP, I don't think it's supposed to appear on the desktop. If you can change your camera to USB storage mode, then it will. If I understand PTP correctly, it's never mounted as a storage device. Instead, it's communicated with through the PTP protocol. Just as you'd never expect a network connection or printer to get mounted a device using PTP won't either. 

Even though it's not mounted, you can see if it gets detected when you connect it. Plug it in, then run "dmesg | tail" and see what the output is. It will hopefully tell you some place in /dev, and you can work on it from there.

---

### Post by jdway on 2005-12-28
[4421443.759000] APIC error on CPU0: 02(02)
[4421469.399000] APIC error on CPU0: 02(02)
[4421475.045000] APIC error on CPU0: 02(02)
[4421488.712000] APIC error on CPU0: 02(02)
[4421587.226000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=220.168.158.10 DST=24.98.150.206 LEN=381 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=37537 DPT=1033 LEN=361
[4421587.228000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=220.168.158.10 DST=24.98.150.206 LEN=381 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=37537 DPT=1029 LEN=361
[4421619.055000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=212.24.144.73 DST=24.98.150.206 LEN=52 TOS=0x00 PREC=0x00 TTL=44 ID=54444 DF PROTO=TCP SPT=1917 DPT=28615 WINDOW=65535 RES=0x00 SYN URGP=0
[4421622.068000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=212.24.144.73 DST=24.98.150.206 LEN=52 TOS=0x00 PREC=0x00 TTL=44 ID=55261 DF PROTO=TCP SPT=1917 DPT=28615 WINDOW=65535 RES=0x00 SYN URGP=0
[4421628.068000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=212.24.144.73 DST=24.98.150.206 LEN=52 TOS=0x00 PREC=0x00 TTL=44 ID=57503 DF PROTO=TCP SPT=1917 DPT=28615 WINDOW=65535 RES=0x00 SYN URGP=0
[4421766.885000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=61.130.254.109 DST=24.98.150.206 LEN=404 TOS=0x00 PREC=0x00 TTL=106 ID=11247 PROTO=UDP SPT=4643 DPT=1434 LEN=384


This is what I see when I type dmesg|tail into the terminal. I have no idea what this does or means so where do I go from here?

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=jdway][4421443.759000] APIC error on CPU0: 02(02)
[4421469.399000] APIC error on CPU0: 02(02)
[4421475.045000] APIC error on CPU0: 02(02)
[4421488.712000] APIC error on CPU0: 02(02)
[4421587.226000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=220.168.158.10 DST=24.98.150.206 LEN=381 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=37537 DPT=1033 LEN=361
[4421587.228000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=220.168.158.10 DST=24.98.150.206 LEN=381 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=37537 DPT=1029 LEN=361
[4421619.055000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=212.24.144.73 DST=24.98.150.206 LEN=52 TOS=0x00 PREC=0x00 TTL=44 ID=54444 DF PROTO=TCP SPT=1917 DPT=28615 WINDOW=65535 RES=0x00 SYN URGP=0
[4421622.068000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=212.24.144.73 DST=24.98.150.206 LEN=52 TOS=0x00 PREC=0x00 TTL=44 ID=55261 DF PROTO=TCP SPT=1917 DPT=28615 WINDOW=65535 RES=0x00 SYN URGP=0
[4421628.068000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=212.24.144.73 DST=24.98.150.206 LEN=52 TOS=0x00 PREC=0x00 TTL=44 ID=57503 DF PROTO=TCP SPT=1917 DPT=28615 WINDOW=65535 RES=0x00 SYN URGP=0
[4421766.885000] Inbound IN=eth0 OUT= MAC=00:0d:61:69:c2:c5:00:30:b8:c2:b4:40:08:00 SRC=61.130.254.109 DST=24.98.150.206 LEN=404 TOS=0x00 PREC=0x00 TTL=106 ID=11247 PROTO=UDP SPT=4643 DPT=1434 LEN=384


This is what I see when I type dmesg|tail into the terminal. I have no idea what this does or means so where do I go from here?[/QUOTE]

It is just showing firewall-related statistics.  If there was anything in there about it creating a device node, it looks like it was earlier in the log.

Try the following command to see if your system at least recognizes that the camera is plugged into the usb port:
```

$ lsusb

```

If you see the camera there, then one possible way to figure out if a device node was created is to compare a list of the /dev folder contents before and after you plug in the camera.  For example:
```

$ ls /dev > unplugged.txt

```
Plug in camera.  Wait about 10 seconds.
```

$ ls /dev > plugged.txt
$ sort plugged.txt unplugged.txt | uniq -u

```
If there is any output, that means the device was created between the time you took the first listing and the second listing.  That device is what you would need to mount.

If no device is being created, then we probably have to explore the manufacturer's support center to find out if they have some sort of Linux compatible driver.

---

### Post by jdway on 2005-12-28
I sent an emal to hp and recieved the following reply:

I gather from your e-mail that you are using Linux Ubuntu operating
system amd you are unable to unload images to the computer.

I understand your concern and assure you that we leave no stone 
unturned to address the issue at the earliest.

We appreciate your interest in HP Photosmart product, software/drivers 
for your computer/camera.  Currently, HP offers drivers for all 
Photosmart products in Windows 98.  Drivers for selected products 
are available for Windows 95/ME, Windows NT/2000, Windows XP and 
Macintosh OS.  Currently HP does not support any Photosmart product 
in the Linux operating system.

Since HP does not make a photosmart driver for linux, does that mean that I am screwed?

---

### Post by xmastree on 2005-12-28
Does it use internal memory or a memory card?
If it's a card why not just get a card reader? It's more convenient, and saves your camera batteries.

---

### Post by zoiks on 2005-12-28
[QUOTE=jdway]
Since HP does not make a photosmart driver for linux, does that mean that I am screwed?[/QUOTE]

Not necessarily.  As usual, the hardware manufacturers are lazy schmucks and the Linux folk have to make the stuff work themselves.

Not all cameras, especially older ones, support usb mass storage mode.  When they do, the storage device will generally show up as /dev/sda or /dev/sda1 (or /dev/sdb, etc.) and should get automounted by ubuntu.

When they don't act as simple storage devices, gphoto (installable as gphoto2) may be able to help.  Your camera isn't listed on this page:

[http://www.teaser.fr/~hfiguiere/linux/digicam.html](http://www.teaser.fr/~hfiguiere/linux/digicam.html)

but similar model numbers are there, so it might actually work.  It may be a simple matter of using "gphoto2 -P" to get all the pictures out of the camera.   (check man gphoto2 for help) That's how I used it.  My Nikon E990 worked great with gphoto2.  My wild guess is that it will work, but honestly I really don't know.

---

### Post by lsd on 2007-01-13
I've just adquired an HP PhotoSmart M627. In the USB configuration menu you can switch between PTP mode (that it doesn't works as a normal user, only root, and with GThumb) and Disk Device mode.

Now I can explore with Thunar an automounted sda1 disk. I suppose that Nautilus will do the same on the desktop.

---

