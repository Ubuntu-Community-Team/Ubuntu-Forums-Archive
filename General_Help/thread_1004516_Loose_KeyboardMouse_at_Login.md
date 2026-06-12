---
title: "Loose Keyboard/Mouse at Login"
date: 2008-12-07
forum: General Help
---

### Post by letubenaiah on 2008-12-07
Yesterday I updated my ubuntu system from 8.04 to 8.10 and I have run into a problem.  Every time after the initial reboot when ever I restart the computer I loose the use of the USB keyboard and mouse at the login screen.  They work in the boot menues but once I reach the login screen I get nothing.  However, if I wait for about 2 or 3 minutes they come back and everything is fine.  

I've tried uncommenting the section about keyboad and mouse in xorg.conf and also running "dpkg-reconfigure console-setup" but neither of these worked.  Anyone have any idea?

Thanks!

---

### Post by silverwolf636 on 2008-12-08
Exact same scenerio here too.  From the upgrade to the mouse and keyboard problem.  Hmmm. Hope there's a fix.

---

### Post by letubenaiah on 2008-12-09
I'm still having the same problem.  Today when I started up I received a string of error messages about devices descriptor errors.  This is what I could catch of them:

```
usb 4-1 device descriptor read/8, error -110
```

Once I got the computer to boot I checked the output of dmesg and this is part of that output.

```
[  211.148438] usb 7-2: reset high speed USB device using ehci_hcd and address 2
[  284.108034] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  299.220028] usb 1-1: device descriptor read/64, error -110
[  314.436026] usb 1-1: device descriptor read/64, error -110
[  314.652025] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  329.768022] usb 1-1: device descriptor read/64, error -110
[  344.984041] usb 1-1: device descriptor read/64, error -110
[  345.196041] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  350.217678] usb 1-1: device descriptor read/8, error -110
[  355.337800] usb 1-1: device descriptor read/8, error -110
[  355.552052] usb 7-2: reset high speed USB device using ehci_hcd and address 2
[  355.796035] usb 1-1: new full speed USB device using uhci_hcd and address 10
[  360.817935] usb 1-1: device descriptor read/8, error -110
[  365.942058] usb 1-1: device descriptor read/8, error -110
[  366.044032] hub 1-0:1.0: unable to enumerate USB device on port 1

```

Any ideas on how to fix this would be really appreciated.

---

### Post by linux_tech on 2008-12-09
Is this a laptop?  What make and model?

---

### Post by linux_tech on 2008-12-09
```
sudo gedit /boot/grub/menu.lst
```
Try replacing a line:
# defoptions=quiet splash
by this one:
# defoptions=quiet splash acpi=force irqpoll
save, quit and the run
```
sudo update-grub
```

---

### Post by letubenaiah on 2008-12-09
This did not work.  Unrelated to the edit to menu.lst it has gotten worse, now instead of getting to the login screen and just waiting a few minutes it crashes during the loading screen before the login screen and gives the error messages given above.  However, if I unplug one of my printers everything works fine.  

Also if I plug the printer back in but to a different port everything breaks again.

I am using a Dell Dimension E520 Desktop.

> **linux_tech said:**
> ```
sudo gedit /boot/grub/menu.lst
```
Try replacing a line:
# defoptions=quiet splash
by this one:
# defoptions=quiet splash acpi=force irqpoll
save, quit and the run
```
sudo update-grub
```

---

### Post by linux_tech on 2008-12-09
To clarify, if the printer is unplugged does the mouse and keyboard work?

---

### Post by letubenaiah on 2008-12-09
Yes they work, and there is not a delay.  They work as soon as I get to the login sreen.

> **linux_tech said:**
> To clarify, if the printer is unplugged does the mouse and keyboard work?

---

### Post by gijsterbeek on 2009-02-20
I've started to have exactly these kinds of problems since january 2009. Most of the time everything works fine, but sometimes all my USB devices fail to start. 

I've tried/read this:
[http://ubuntuforums.org/showthread.php?t=257512](http://ubuntuforums.org/showthread.php?t=257512)
[http://ubuntuforums.org/showthread.php?t=840177](http://ubuntuforums.org/showthread.php?t=840177)
[http://forums.fedoraforum.org/showthread.php?t=164996](http://forums.fedoraforum.org/showthread.php?t=164996)
..and many more, 

but to no avail. Some forum (couldn't find it anymore) suggested there might be static dust inside one of the USB connectors, so I removed all the dust, but this also doesn't seem to work permanently. Also, unplugging the mouse while the errors are being displayed and then replugging it, sometimes helps. 

But there just doesn't seem to be any predictability in these solutions. Does anybody have the same problem? Or/and a solution?

---

### Post by gijsterbeek on 2009-02-20
additional info:

lspci says:
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
04:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

lsusb says nothing (terminal hangs?), but after +/- 90 seconds:
Bus 005 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 001 Device 005: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | grep usb says:

[    2.141276] usbcore: registered new interface driver usbfs                                                          
[    2.141297] usbcore: registered new interface driver hub                                                            
[    2.141324] usbcore: registered new device driver usb                                                               
[    2.200564] usb usb1: configuration #1 chosen from 1 choice                                                         
[    2.412424] usb usb2: configuration #1 chosen from 1 choice                                                         
[    2.520026] usb 1-1: new low speed USB device using uhci_hcd and address 2                                          
[    2.616508] usb usb3: configuration #1 chosen from 1 choice                                                         
[    2.696706] usb 1-1: configuration #1 chosen from 1 choice                                                          
[    2.720338] usb usb4: configuration #1 chosen from 1 choice                                                         
[    2.808030] usb 1-2: new low speed USB device using uhci_hcd and address 3                                          
[    2.948809] usb usb5: configuration #1 chosen from 1 choice                                                         
[    2.955490] usb 1-2: device descriptor read/all, error -71                                                          
[    3.268076] usbcore: registered new interface driver hiddev                                                         
[    3.268287] usb 1-1: USB disconnect, address 2                                                                      
[    3.628039] usb 5-4: new high speed USB device using ehci_hcd and address 4                                         
[   18.740526] usb 5-4: device descriptor read/64, error -110                                                          
[   33.956025] usb 5-4: device descriptor read/64, error -110                                                          
[   34.172032] usb 5-4: new high speed USB device using ehci_hcd and address 5                                         
[   49.284026] usb 5-4: device descriptor read/64, error -110                                                          
[   59.088026] usb 5-8: new high speed USB device using ehci_hcd and address 6                                         
[   59.222082] usb 5-8: configuration #1 chosen from 1 choice                                                          
[   59.222361] usbcore: registered new interface driver usbhid                                                         
[   59.222364] usbhid: v2.6:USB HID core driver                                                                        
[   59.460024] usb 1-1: new low speed USB device using uhci_hcd and address 5                                          
[   59.636731] usb 1-1: configuration #1 chosen from 1 choice                                                          
[   59.652828] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[   59.653334] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1              
[   59.892025] usb 1-2: new low speed USB device using uhci_hcd and address 6                                          
[   60.068717] usb 1-2: configuration #1 chosen from 1 choice                                                          
[   60.086910] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2  
[   60.087388] input,hidraw1: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.0-2             
[   60.088057] usbcore: registered new interface driver libusual                                                       
[   60.096215] usb-storage: device found at 6                                                                          
[   60.096218] usb-storage: waiting for device to settle before scanning                                               
[   60.096231] usbcore: registered new interface driver usb-storage                                                    
[   65.096224] usb-storage: device scan complete                                                                       
[   65.340031] usb 5-3: new high speed USB device using ehci_hcd and address 7                                         
[   80.452081] usb 5-3: device descriptor read/64, error -110                                                          
[   95.671340] usb 5-3: device descriptor read/64, error -110                                                          
[   95.888040] usb 5-3: new high speed USB device using ehci_hcd and address 8                                         
[  111.008057] usb 5-3: device descriptor read/64, error -110                                                          
[  126.220046] usb 5-3: device descriptor read/64, error -110                                                          
[  126.436771] usb 5-3: new high speed USB device using ehci_hcd and address 9                                         
[  131.456065] usb 5-3: device descriptor read/8, error -110                                                           
[  136.576134] usb 5-3: device descriptor read/8, error -110                                                           
[  136.792023] usb 5-3: new high speed USB device using ehci_hcd and address 10                                        
[  141.812072] usb 5-3: device descriptor read/8, error -110                                                           
[  146.932138] usb 5-3: device descriptor read/8, error -110                                                           
[  147.360163] usb 2-1: new full speed USB device using uhci_hcd and address 2                                         
[  162.472025] usb 2-1: device descriptor read/64, error -110                                                          
[  177.688029] usb 2-1: device descriptor read/64, error -110                                                          
[  177.904028] usb 2-1: new full speed USB device using uhci_hcd and address 3                                         
[  193.024042] usb 2-1: device descriptor read/64, error -110                                                          
[  208.244023] usb 2-1: device descriptor read/64, error -110                                                          
[  208.464024] usb 2-1: new full speed USB device using uhci_hcd and address 4                                         
[  213.485512] usb 2-1: device descriptor read/8, error -110                                                           
[  218.605697] usb 2-1: device descriptor read/8, error -110
[  218.820038] usb 2-1: new full speed USB device using uhci_hcd and address 5
[  223.841895] usb 2-1: device descriptor read/8, error -110
[  228.961082] usb 2-1: device descriptor read/8, error -110
[  232.140978] usb 2-1: new full speed USB device using uhci_hcd and address 6
[  247.256521] usb 2-1: device descriptor read/64, error -110
[  262.472523] usb 2-1: device descriptor read/64, error -110
[  262.688031] usb 2-1: new full speed USB device using uhci_hcd and address 7
[  277.805705] usb 2-1: device descriptor read/64, error -110
[  293.020025] usb 2-1: device descriptor read/64, error -110
[  293.236027] usb 2-1: new full speed USB device using uhci_hcd and address 8
[  298.257995] usb 2-1: device descriptor read/8, error -110
[  303.388017] usb 2-1: device descriptor read/8, error -110
[  303.604028] usb 2-1: new full speed USB device using uhci_hcd and address 9
[  308.629379] usb 2-1: device descriptor read/8, error -110
[  313.749570] usb 2-1: device descriptor read/8, error -110

---

