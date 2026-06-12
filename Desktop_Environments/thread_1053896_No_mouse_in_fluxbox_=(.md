---
title: "No mouse in fluxbox =("
date: 2009-01-29
forum: Desktop Environments
---

### Post by kaoticsnow on 2009-01-29
I have a box I have running at work with ubuntu server and rather then reinstall to Ubuntu desktop I was hoping to just get fluxbox up and running on it. got it running but I cant move the mouse, It is detected as you can see any ideas on how to get my mouse working?

```
Jan 29 02:26:11 Bender kernel: [  103.950059] usb 1-4: new low speed USB device using ohci_hcd and address 2
Jan 29 02:26:12 Bender kernel: [  104.177470] usb 1-4: configuration #1 chosen from 1 choice
Jan 29 02:26:12 Bender kernel: [  104.229308] usbcore: registered new interface driver hiddev
Jan 29 02:26:12 Bender kernel: [  104.235772] input: Logitech as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input5
Jan 29 02:26:12 Bender kernel: [  104.332604] input,hidraw0: USB HID v1.00 Mouse [Logitech] on usb-0000:00:0b.0-4
Jan 29 02:26:12 Bender kernel: [  104.332632] usbcore: registered new interface driver usbhid
Jan 29 02:26:12 Bender kernel: [  104.332636] usbhid: v2.6:USB HID core driver
```

---

### Post by Flotter on 2009-01-29
Sounds like you might be using an Nvidia video card.  I got that mouse pointer problem all the time until I dug into my /etc/X11/xorg.conf and added:

        Option          "HWCursor"      "Off"

to the section talking about the video card:

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "NVIDIA GeForce 6 Series"
        Busid           "PCI:0:5:0"
        Driver          "nv"
        Screen  0
        Vendorname      "NVIDIA"
        Option          "HWCursor"      "Off"
EndSection


Then, just restart your X by CTRL-ALT-BACKSPACE and relog, you should have it.

---

