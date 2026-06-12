---
title: "USB devices not recognised"
date: 2011-03-15
forum: Desktop Environments
---

### Post by foontas on 2011-03-15
I'm running ubuntu 10.10

Any usb devices inserted after bootup aren't being automounted and opened. For the life of me, after much googling, I can't get them to work. the ehci_hcd, uhci_hcd and ohci_hcd modules are not loaded, but those were from some old posts, and I don't know how relevant they are to me.

But if I insert the usb before startup, ubuntu now recognises and automounts any usb device.

before the recent kernel update ( **.28) my wifi dongle would be recognised. but after, it seems as it too isn't being recognised.

for the meantime, I am keeping a small unused usb device plugged in the back of the tower.

can anyone help me?

much appreciated.

---

### Post by Mark_in_Hollywood on 2011-03-15
If you have an Ubuntu CD or DVD and can boot into it, I would use GParted and have a look at those USB sticks partition and formatting. If you are them on a Windows machine as well, it's better to format them to NTFS. If they are SanDisk devices, SanDisk uses a small program and can be removed, but I've lost track of that tech info. Please try netsearching for it. I hope this helps.

---

### Post by foontas on 2011-03-20
Sorry about the late reply.

still getting used to subscribing to threads and what not.

what will I be looking for through Gparted? 

These usb drives worked on another installation of ubuntu 10.10, but not my current one. wouldn't the problem lie within this current installation of ubuntu?

---

### Post by Grafens on 2011-03-20
I had similar issues with automount usb's. Have you tried going to Places > Computer > Right click the usb icon and mount it that way.
Also you could try reformatting your blank usb to a different file type like FAT using Gparted and see if that helps.

Grafens

---

### Post by foontas on 2011-03-20
I can't even see the usb in Computer. The light on the usb is on, so it is connected.

My current work-around is to leave a small unused usb drive in the back of the tower so that the computer starts with a usb in it already. for some reason, that works, and usb drives will mount, and my wireless dongle will be recognised.

If I have no usb drive connected (but the wireless dongle still attached) then no usb drive or the wireless dongle will be recognised and I can't mount any usb drive in and have no internet.

---

### Post by Mark_in_Hollywood on 2011-05-22
Open a terminal. If you don't have the "Terminal" on your Desktop or Panel, pulldown the Applications Menu to Accessories and find both Terminal and Text Editor (or maybe it says: Gedit). Right click on each and add them to your desktop.

Open the "terminal" by double clicking. Then type 

lsusb

and post the output of that in this thread of yours. I'm slow, but I'll be waiting.

---

### Post by feci on 2011-05-28
Hello everybody,

I have the same problem as Mark, although I didn't experiment with plugging in a usb before booting.
I'm also using Ubuntu 10.10 and usb drives and cardreaders were working at the beginning. At some point in the last 2 weeks usbs are not working anymore.
As Mark already said the LEDs on the device are on, I get a message in dmesg "usb 1-3.4: new high speed USB device using ehci_hcd and address 7", but no device is created in /dev/. As a result the device is not visible in gnome in the places menu and also can't be mounted by hand.
I've read in some forums that ehci should be disabled, and I even tried it, but it didn't work.
And for sure it's a HW or partition problem, because the same devices are working on the same computer when booting my old Ubuntu 8.10.

Also doing lsusb as a normal user, the device ID is not in the list, but when running sudo lsusb the device is visible:
feci@GEP2:/proc/bus$ lsusb
Bus 008 Device 002: ID 045e:0750 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

vs.

feci@GEP2:/proc/bus$ sudo lsusb
[sudo] password for feci: 
Bus 008 Device 002: ID 045e:0750 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 04e8:6032 Samsung Electronics Co., Ltd     <-- my external SAMSUNG drive
Bus 001 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any help is appreciated.

---

### Post by Mark_in_Hollywood on 2011-05-31
I must now ask for the model of the Samsung drive, too. In the meantime, while this post is a "long road to hoe", it might be the answer.

Please note the date of this as 2008. I'm not expert (or even informed enough) to say whether this information is out of date or not, but it's, so to speak, a start:


[http://ubuntuforums.org/showthread.php?t=1020604](http://ubuntuforums.org/showthread.php?t=1020604)

---

