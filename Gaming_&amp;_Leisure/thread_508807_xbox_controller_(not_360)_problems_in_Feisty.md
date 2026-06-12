---
title: "xbox controller (not 360) problems in Feisty"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by mrtof on 2007-07-24
I am having trouble with my Xbox (non 360) controller. I used to use it with Debian but since I switched to Ubuntu it does not work anymore. Nothing appears as /dev/input/js*

Please help.

I am using a non Microsoft wireless self modified Xbox (not 360) controller. It works fine in XP, so I know the hardware is good condition.

My Linux version: 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

This is the output of dmesg after plugging in the controller::
```
[  119.986717] usb 1-5: new full speed USB device using ohci_hcd and address 3
[  120.173272] usb 1-5: configuration #1 chosen from 1 choice
[  120.176243] hub 1-5:1.0: USB hub found
[  120.179198] hub 1-5:1.0: 3 ports detected
[  120.483665] usb 1-5.1: new full speed USB device using ohci_hcd and address 4
[  120.580562] usb 1-5.1: configuration #1 chosen from 1 choice
[  120.687445] usbcore: registered new interface driver xpad
[  120.687734] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
```

This the output of /var/log/messages after plugging in the controller:
```
Jul 24 14:38:44 grosbois gconfd (tom-5427): Resolved address "xml:readwrite:/home/tom/.gconf" to a writable configuration source at position 0
Jul 24 14:39:01 grosbois kernel: [  119.986717] usb 1-5: new full speed USB device using ohci_hcd and address 3
Jul 24 14:39:02 grosbois kernel: [  120.173272] usb 1-5: configuration #1 chosen from 1 choice
Jul 24 14:39:02 grosbois kernel: [  120.176243] hub 1-5:1.0: USB hub found
Jul 24 14:39:02 grosbois kernel: [  120.179198] hub 1-5:1.0: 3 ports detected
Jul 24 14:39:02 grosbois kernel: [  120.483665] usb 1-5.1: new full speed USB device using ohci_hcd and address 4
Jul 24 14:39:02 grosbois kernel: [  120.580562] usb 1-5.1: configuration #1 chosen from 1 choice
Jul 24 14:39:02 grosbois kernel: [  120.687445] usbcore: registered new interface driver xpad
Jul 24 14:39:02 grosbois kernel: [  120.687734] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
```

I tried a logitech gamepad and it worked fine: it created the proper inputs:
```
[ 4974.797001] usb 2-5: new low speed USB device using ohci_hcd and address 7
[ 4975.068328] usb 2-5: configuration #1 chosen from 1 choice
[ 4975.125212] input: Logitech Logitech Cordless RumblePad 2 as /class/input/input8
[ 4975.125254] input: USB HID v1.10 Gamepad [Logitech Logitech Cordless RumblePad 2] on usb-0000:00:02.0-5
```

Why is the Xbox controller not working while the Logitech controller works?

Thank you for your help.

---

### Post by mrtof on 2007-07-24
After disconnecting the Xbox controller and then reconnecting it, I get a different dmesg than before: 
```
[ 5145.132097] usb 2-5: new full speed USB device using ohci_hcd and address 8
[ 5145.333014] usb 2-5: configuration #1 chosen from 1 choice
[ 5145.335988] hub 2-5:1.0: USB hub found
[ 5145.338940] hub 2-5:1.0: 3 ports detected
[ 5145.688332] usb 2-5.1: new full speed USB device using ohci_hcd and address 9
[ 5145.808201] usb 2-5.1: configuration #1 chosen from 1 choice
```

Is this normal?

---

### Post by po0f on 2007-07-26
mrtof,

That's weird that it recognized it but it didn't work, then failed to recognize it a second try.  Have you tried using a different USB port?

---

### Post by Nachowarrior on 2007-07-29
hey, i hooked up some spare xbox ports to my pc via the usb pins on my mobo... i hooked a logitec wireless controller to it and if i go into the hardware information it reads /dev/input/event7   I just started this project this evening... so i don't know much...

i'm also using fiesty.

and you prolly already know this but if you need a program to access your controller driver you'll need to 

sudo chown "your name" /dev/input/event7  

or whatever your hardware line ends up showing.... maybe run a chown on it anyway to see if it changes anything? I dunno man... my logitec works fine...   oh... and double check your wiring?

on the same subject... almost... i was trying to get my controller to work with snes9express and when i go to the button config it says "driver too old"  any ideas?

---

### Post by Nachowarrior on 2007-07-29
one more thought.... i saw the "usb hub" line in your recent post... could you switch it to a direct hookup and see if that works? no hub?

---

