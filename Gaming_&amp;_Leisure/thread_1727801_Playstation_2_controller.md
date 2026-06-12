---
title: "Playstation 2 controller?"
date: 2011-04-12
forum: Gaming &amp; Leisure
---

### Post by Raevyn on 2011-04-12
Hai

I am very confused.. I have both a PS2 controller and PS3 controller pluggedi in via USB and neither seem to be seen by my ubuntu 10 installation. I did some searching online and I kept seeing i needed to install joystick and jscalibrator right, but jscalibrator isnt found! Joystick was and installed. 

How do I see if Linux sees it? Or even calibrate it? EIther of them really.

Oh! So I was just on my windows virtual machine and went up to connect my iphone to it, and i saw that my ps3 controller was visible, but not connected to windows. so that means linux sees it.. but how do i configure it?

UGh okay sorry... i just changed the ps2 controller and now the virtual machine sees it.. i still cant use it though.

---

### Post by sakuramboo on 2011-04-13
When it's plugged in, open a terminal and run...

lsusb

This should tell you if it's recognized. If it is, then check the output from dmesg to see if there were any errors with the device or it's drivers.

The lessen the amount of output, try something like

dmesg | grep <device name as displayed in lsusb>

or, you can try the device ID instead.

or, make sure it is unplugged and run...

dmesg | tail -f

And then plug it in and see what it says.

Also, what adaptor are you using for the PS2 controller?

---

### Post by Raevyn on 2011-04-13
Hello :)

Okay I did that grep command and received the following:

raevyn@Caeli:~$ dmesg | grep 1345:0003
[ 2185.274734] generic-usb 0003:1345:0003.0003: input,hidraw2: USB HID v1.10 Joystick [LuenKeung Co.,Ltd USB  Joystick] on usb-0000:00:13.0-3/input0

Then I did the command you suggested once it is disconnected and received back:

raevyn@Caeli:~$ dmesg | tail -f
[  411.398188] /dev/vmnet: open called by PID 2595 (vmware-vmx)
[  411.398217] device eth1 entered promiscuous mode
[  411.398225] bridge-eth1: enabled promiscuous mode
[  411.398231] /dev/vmnet: port on hub 0 successfully opened
[ 2185.070095] usb 5-3: new low speed USB device using ohci_hcd and address 2
[ 2185.274506] input: LuenKeung Co.,Ltd USB  Joystick as /devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input4
[ 2185.274734] generic-usb 0003:1345:0003.0003: input,hidraw2: USB HID v1.10 Joystick [LuenKeung Co.,Ltd USB  Joystick] on usb-0000:00:13.0-3/input0
[ 2429.828993] hub 5-0:1.0: port 3 disabled by hub (EMI?), re-enabling...
[ 2429.829005] usb 5-3: USB disconnect, address 2
[ 2430.640105] hub 5-0:1.0: unable to enumerate USB device on port 3

I have NO idea what all that means LOL. Hopefully you do?

The adapter I am using is listed in both that Linux output AND in VMware as LuenKeung Co.,Ltd USB  Joystick. Its a little USB dongle that lets me plug in a playstation 2 controller.

---

### Post by sakuramboo on 2011-04-13
Has that device ever worked before?

What dmesg is telling you is that you plug it in, it recognizes it, but something happens that makes the usb hub disconnect. That would normally happen with faulty hardware.

It is either a problem with the device or the hub. My feeling is with the hub because this problem was seen elsewhere. Do you have an external usb hub you can try it out on?

---

### Post by Raevyn on 2011-04-14
I have other devices that are plugged in that seem work, both around and in the same port I was using :( But I have tried plugging it in the front USB ports now and it doesnt seem to make any dif but I do get different output!

raevyn@Caeli:~$ dmesg | tail -f
[13459.760165] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[13459.765280] ata3.00: configured for UDMA/133
[13459.765291] ata3: EH complete
[13459.770057] ata5.00: configured for UDMA/133
[13459.770069] ata5: EH complete
[13459.792319] ata4.00: configured for UDMA/133
[13459.792329] ata4: EH complete
[13463.430102] usb 5-1: new low speed USB device using ohci_hcd and address 2
[13463.635246] input: LuenKeung Co.,Ltd USB  Joystick as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input4
[13463.635465] generic-usb 0003:1345:0003.0003: input,hidraw2: USB HID v1.10 Joystick [LuenKeung Co.,Ltd USB  Joystick] on usb-0000:00:13.0-1/input0
raevyn@Caeli:~$ 

Does that seem to look better? I know I still cant play any games with the controller.

---

### Post by Raevyn on 2011-04-14
Oh so I just ran windows and it not only sees the device, but when i go to its properties i can use the round sticks now, not just the buttons, so somthing must be off with the usb?

---

### Post by sakuramboo on 2011-04-14
Yes, the other output looks much better. It gets assigned the device input0 which is what it should be getting.

What games are you trying to use it with? Not all games support game pads. They might off some rudimentary support, but not all.

Also, do you have a spare machine around that you can test it on?

---

### Post by Raevyn on 2011-04-20
Unfortunately I dont have another machine I can test the controller on, but maybe you are right about not having a game that supports joysticks. I will see if I can find something to test it out :)

---

### Post by Shazzner on 2011-04-20
You can try to install xserver-xorg-input-joystick this will allow your joystick/gamepad to controller your mouse. Easy way to test.

Just be sure to uninstall it when you get tired of it, because it will send mouse events while you're playing a game.

I've got a ps1 controller working using an adapter they sold at radio shack for a long time.

---

### Post by abbyjhon on 2011-04-21
Thanks for info....

---

### Post by Raevyn on 2011-04-21
Thank you though how do I turn it on? I found the app in the Ubuntu software repository but when I plug in my controller.. nothing seems to happen.

---

### Post by Raevyn on 2011-04-21
Thank you though how do I turn it on? I found the app in the Ubuntu  software repository but when I plug in my controller.. nothing seems to  happen.

---

