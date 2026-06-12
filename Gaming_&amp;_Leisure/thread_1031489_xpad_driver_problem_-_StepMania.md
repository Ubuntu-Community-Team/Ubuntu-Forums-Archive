---
title: "xpad driver problem - StepMania"
date: 2009-01-05
forum: Gaming &amp; Leisure
---

### Post by svancouw on 2009-01-05
I've posted this to the StepMania forum but have not gotten any suggestions.

I installed StepMania 3.95 in Ubuntu Intrepid (8.10), and after some work got all the deps installed and am able to reliably run the program (although I do have to run it with sudo or it doesn't run).

My problem right now is that, even though the xpad module is loaded in the kernel (verified) SM will not allow me to map the pad. I can see that the pad is recognized when plugged in via the (badly named) Magic Joy Box xBox and PS3 USB adapter (see console text showing this at the end of the post generated when plugged in).

Ubuntu interprets the commands from the pad as a mouse, and I can only get it to do right-click and left-click commands. When I try to run the joystick calebrator (jscalebrator), it doesn't seem to see the pad activity so I don't save the settings.

Do any of you have any ideas on what I can do to get SM to work with the pad? I've searched and read posts for over an hour and haven't found anything useful.

At the moment I'm thinking that I may need a different USB adapter (either PS2 or xBox... my pads have both connectors).

Thank you ahead of time.


/var/log/messages entries when pad adapter is plugged in (this is all from a single event):

Jan 1 18:52:27 Linux-MediaPC kernel: [ 1472.120034] usb 2-2: new full speed USB device using ohci_hcd and address 9
Jan 1 18:52:27 Linux-MediaPC kernel: [ 1472.368606] usb 2-2: configuration #1 chosen from 1 choice
Jan 1 18:52:27 Linux-MediaPC kernel: [ 1472.371391] hub 2-2:1.0: USB hub found
Jan 1 18:52:27 Linux-MediaPC kernel: [ 1472.374206] hub 2-2:1.0: 4 ports detected
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1472.705143] usb 2-2.1: new full speed USB device using ohci_hcd and address 10
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1472.813417] usb 2-2.1: configuration #1 chosen from 1 choice
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1472.822252] hub 2-2.1:1.0: USB hub found
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1472.825282] hub 2-2.1:1.0: 3 ports detected
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1473.137103] usb 2-2.2: new low speed USB device using ohci_hcd and address 11
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1473.251390] usb 2-2.2: configuration #1 chosen from 1 choice
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1473.268423] hiddev97hidraw2: USB HID v1.00 Device [WiseGroup.,Ltd TigerGame XBOX+PS2+GC Game Controller Adapter] on usb-0000:00:03.0-2.2
Jan 1 18:52:28 Linux-MediaPC kernel: [ 1473.350088] usb 2-2.1.1: new full speed USB device using ohci_hcd and address 12
Jan 1 18:52:29 Linux-MediaPC kernel: [ 1473.462499] usb 2-2.1.1: configuration #1 chosen from 1 choice
Jan 1 18:52:29 Linux-MediaPC kernel: [ 1473.467700] input: RedOctane Xbox Dance Pad as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2.1/2-2.1.1/2-2.1.1:1.0/input/input8

---

### Post by brainw0rm on 2009-01-31
hi there.  has there been any resolution for the problem?  i am having an identical problem (ubuntu 8.10 as well), with essentially identical output from dmesg when plugging in the gamepad.  

i've searched the web for hours now, with no resolution in sight.

thanks.

---

### Post by svancouw on 2009-01-31
Unfortunately I have not found a solution. I've come to the conclusion that it is likely a problem with my pad to USB adapter. It'll probably still work in Windows, but it's not playing nice with Linux.

New compatible adapters are hard to find, so I am planning on converting the xbox adapter on one of my pads to usb and plugging it straight into my system. Hopefully that will solve the problem and still let me use multiple pads at once.

If I'm able to get to that soon I'll post the results here, but I've been pretty busy lately.

---

