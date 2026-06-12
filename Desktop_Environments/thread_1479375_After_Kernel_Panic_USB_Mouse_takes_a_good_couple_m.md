---
title: "After Kernel Panic: USB Mouse takes a good couple minutes to respond"
date: 2010-05-10
forum: Desktop Environments
---

### Post by Argeroth on 2010-05-10
Hello,
   I have just done a fresh install of Lucid Linux 64bit. Installation went very well. I ran into an instance of kernel panic while setting up skype. I had a windows XP VM up and running in the background at the time as well.
   Now when I start up it takes a good few minutes for my usb mouse to respond.  Its like its not being recognized.  Afer a couple minutes it does begin to respond.  I've noticed that when I boot into grub the lights on my mouse come on, but then when I select the current kernel (LUCID) or my previous installation which I have on another partition I get the same error now regardless of which partition i boot to.  When I boot into Windows 7 everything is fine.

Anyone have some insights?

using dmesg in the console terminal gives me the following:

[   32.420543] usb 1-3: device descriptor read/64, error -110
[   32.650538] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   47.760625] usb 1-3: device descriptor read/64, error -110
[   63.000720] usb 1-3: device descriptor read/64, error -110
[   63.230716] usb 1-3: new high speed USB device using ehci_hcd and address 4
[   73.650782] usb 1-3: device not accepting address 4, error -110
[   73.770786] usb 1-3: new high speed USB device using ehci_hcd and address 5
[   84.200852] usb 1-3: device not accepting address 5, error -110
[   84.200869] hub 1-0:1.0: unable to enumerate USB device on port 3
[   84.610857] usb 2-3: new high speed USB device using ehci_hcd and address 2
[   84.792320] usb 2-3: configuration #1 chosen from 1 choice
[   84.893682] usbcore: registered new interface driver snd-usb-audio
[   84.940825] Linux video capture interface: v2.00
[   84.949720] uvcvideo: Found UVC 1.00 device USB2.0_Camera (093a:2700)
[   84.959652] input: USB2.0_Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input5
[   84.959706] usbcore: registered new interface driver uvcvideo
[   84.959709] USB Video Class driver (v0.1.0)
[   85.130857] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  100.260971] usb 4-1: device descriptor read/64, error -110
[  115.511683] usb 4-1: device descriptor read/64, error -110
[  115.741679] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  130.861146] usb 4-1: device descriptor read/64, error -110
[  146.101239] usb 4-1: device descriptor read/64, error -110
[  146.341241] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  156.751301] usb 4-1: device not accepting address 4, error -110
[  156.871309] usb 4-1: new full speed USB device using uhci_hcd and address 5
[  167.291369] usb 4-1: device not accepting address 5, error -110
[  167.291384] hub 4-0:1.0: unable to enumerate USB device on port 1
[  167.581377] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  167.746064] usb 5-1: configuration #1 chosen from 1 choice
[  167.880925] usbcore: registered new interface driver hiddev
[  167.884003] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.3/input/input6
[  167.884086] generic-usb 0003:0D8C:0008.0001: input,hidraw0: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:1a.2-1/input3
[  167.884108] usbcore: registered new interface driver usbhid
[  167.884111] usbhid: v2.6:USB HID core driver
[  168.083873] usb 5-2: new full speed USB device using uhci_hcd and address 3
[  168.255941] usb 5-2: configuration #1 chosen from 1 choice
[  168.257872] hub 5-2:1.0: USB hub found
[  168.258821] hub 5-2:1.0: 3 ports detected
[  168.543718] usb 8-1: new low speed USB device using uhci_hcd and address 2
[  168.722466] usb 8-1: configuration #1 chosen from 1 choice
[  168.741567] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input7
[  168.741661] generic-usb 0003:046D:C01E.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-1/input0
[  168.992561] usb 5-2.1: new full speed USB device using uhci_hcd and address 4
[  169.123594] usb 5-2.1: configuration #1 chosen from 1 choice
[  169.128754] input: HID 0a5c:4502 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input8
[  169.128867] generic-usb 0003:0A5C:4502.0003: input,hidraw2: USB HID v1.11 Keyboard [HID 0a5c:4502] on usb-0000:00:1a.2-2.1/input0
[  169.202502] usb 5-2.2: new full speed USB device using uhci_hcd and address 5
[  169.323581] usb 5-2.2: configuration #1 chosen from 1 choice
[  169.330642] input: HID 0a5c:4503 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.2/5-2.2:1.0/input/input9
[  169.330745] generic-usb 0003:0A5C:4503.0004: input,hidraw3: USB HID v1.11 Mouse [HID 0a5c:4503] on usb-0000:00:1a.2-2.2/input0
[  169.432415] usb 5-2.3: new full speed USB device using uhci_hcd and address 6
[  169.562452] usb 5-2.3: configuration #1 chosen from 1 choice
[  169.596096] Bluetooth: Core ver 2.15
[  169.596197] NET: Registered protocol family 31
[  169.596198] Bluetooth: HCI device and connection manager initialized

---

### Post by Argeroth on 2010-05-11
Tonight I tried to reinstall Grub 1.98. I also installed all the current updates.  Still no change.  It seems upon selecting to boot from either of my Ubuntu Linux partitions 9.10 or 10.4 right now I am experiencing an issue where my usb bus loses power.  I'm currently running with an i7 920 platform with an asus mother board.  When I boot to either 9.10 or 10.04 it takes a good 3 minutes before my mouse actually works.

I am leaning towards an issue with the way Grub handles the hand off to the kernel.. as the issue has spread to booting my second Ubuntu partition.  I am going try a complete removal and complete re installation of grub and see if there are any changes.  In the worst case I can always do a fresh reinstall again.

---

