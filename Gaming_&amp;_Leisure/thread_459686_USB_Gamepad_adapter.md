---
title: "USB Gamepad adapter"
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by Shoeberto on 2007-05-30
I recently picked this gamepad adapter for Gamcube/PS2/Xbox controllers:
[http://www.futime.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml](http://www.futime.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml)
However, I don't seem to be able to get it to work.

I've looked around quite a bit.  Doing cat /dev/input/js0 returns some strange characters.

dmesg returns this following while plugging the device in:
```
[138161.344644] usb 2-2.1: new full speed USB device using uhci_hcd and address 3
[138161.454809] usb 2-2.1: configuration #1 chosen from 1 choice
[138161.463736] input: HID 19fa:8d91 as /class/input/input13
[138161.463820] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:10.1-2.1
[138161.469747] input: HID 19fa:8d91 as /class/input/input14
[138161.469831] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:10.1-2.1

```
Running jscalibrator returns no input and no programs recognize it as being there.  I've tried both PS1 and PS2 dual shock controllers.  I don't have my Gamecube controllers on hand to test with, nor do I own any Xbox controllers.

Any suggestions?

---

### Post by DarkN00b on 2007-07-13
I just got one of these myself and it seems to work well...except that all the buttons seem to be stuck on rapid fire with my PS controller -- the only thing is that the controller doesn't have rapid fire. This makes LoZ: Minish Cap difficult to play. :)

Have you figured out your problem yet? If so, how did you fix it? If anyone else has any ideas I'd be glad to try 'em.

In case anyone wonders, this thing is a combination PS/XBOX/GC controller adapter / 2-port USB hub.

---

### Post by Contrast on 2007-07-13
If you're content with just being able to use PS2 controllers, you might try [these]("http://www.radioshack.com/product/index.jsp?productId=2348187&cp=2032062&f=Taxonomy%2FRSK%2F2032062&categoryId=2032062&kwCatId=2032062&kw=ps2+adapter&parentPage=search")  - I've used them with the regular PS2 controllers and the Guitar Hero II controller without issue.

---

### Post by DarkN00b on 2007-07-13
Well I kinda already have this one.... :D

If I can't get it to work, I may get one of those. I'll work with this one for a while though, I enjoy the challenge.

---

### Post by DarkN00b on 2007-07-14
I kinda got it to work, but I made a discovery. Jscalibrate totally screws up your gamepad configuration. The D-pad completely quit working. This is because it maps lef-right to *one* axis and up-down to *another* axis. I had to delete my /etc/input/js0 and /etc/input/js1 nodes to get my regular wireless gamepad to work.

I will continue to work with the adapter, but I think this is going to require a driver that doesn't exist for Linux.

---

### Post by synthetic_fenix on 2007-07-21
I'd be interested in getting one of these to work as well, I plan on using it to plug into my mythbox to hook up my DDR pad in order to play Stepmania on my Mythbox.

---

### Post by DarkN00b on 2007-07-21
I'm now convinced that this is going to require a native linux driver. This is because if you watch the output while using jscalibrate, you will notice that for every button press, stick or d-pad movement, there are two signals generated. One when you press the button (or move the stick) and one when you release it. For some reason this creates a "rapid fire" effect when using the controller. Directional buttons like the d-pad or joystick work fine, but as soon as you push for example the button to swing Link's sword it swings like mad and you can't charge up. The adapter comes with a mini-cd with Windows drivers but that doesn't help us linux users much. :-?

If yo use jscalibrate, make sure you don't save the configuration. If your gamepad/joystick doesn't work after using jscalibrate, delete /etc/input/js* and plug in your device again.

---

### Post by aitvo on 2007-07-22
Any luck getting this device to work?

From lsusb:

Bus 002 Device 004: ID 19fa:8d91  

Here's the relevant portion of /var/log/messages:

Jul 22 19:04:30 deathstar kernel: [  556.587205] usb 2-1: new full speed USB device using uhci_hcd and address 7
Jul 22 19:04:31 deathstar kernel: [  556.819752] usb 2-1: configuration #1 chosen from 1 choice
Jul 22 19:04:31 deathstar kernel: [  556.822692] hub 2-1:1.0: USB hub found
Jul 22 19:04:31 deathstar kernel: [  556.825639] hub 2-1:1.0: 4 ports detected
Jul 22 19:04:31 deathstar kernel: [  557.163809] usb 2-1.1: new full speed USB device using uhci_hcd and address 8
Jul 22 19:04:31 deathstar kernel: [  557.281607] usb 2-1.1: configuration #1 chosen from 1 choice
Jul 22 19:04:31 deathstar kernel: [  557.291561] input: HID 19fa:8d91 as /class/input/input10
Jul 22 19:04:31 deathstar kernel: [  557.291620] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:1d.1-1.1
Jul 22 19:04:31 deathstar kernel: [  557.297531] input: HID 19fa:8d91 as /class/input/input11
Jul 22 19:04:31 deathstar kernel: [  557.297669] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:1d.1-1.1

As the other user stated, same effect with a GC controller. Everything is rapid fire, even the dpad.

The Xbox controller portion works great though (since it's probably just a USB remap).

Any insight would be great.

---

### Post by TremerePuck on 2007-08-10
I can't even get the xbox one to work. =o/  Only two joysticks show up when it's plugged in.

---

### Post by aitvo on 2007-08-10
> **TremerePuck said:**
> I can't even get the xbox one to work. =o/  Only two joysticks show up when it's plugged in.

I returned mine, went to radio shack and got the PS2 / USB dongle.

---

### Post by luridsorcerer on 2007-08-16
My controller adapter is on perpetual rapid fire also.  Strange, because it worked fine when I used it with Knoppix...

Honestly, I can't figure out what the deal is with this thing!  Anyone figure anything out?

EDIT: [This thread]("http://ubuntuforums.org/showthread.php?t=512209&highlight=joystick") states that some kernels do this.  It states that kernel 2.6.22 may have this corrected.  I'll probably go try this later.

EDIT2: Finally, I went through the painful and difficult process of compiling my first kernel.  The 2.6.22.1 kernel I built works perfectly with my controller adapter.

---

### Post by DarkN00b on 2007-09-26
I'm running 2.6.22.12 at the moment under Gutsy. I'll have to try this out tomorrow -- I'll get back with y'all.

---

### Post by zergio on 2007-11-02
Freaking perfect, in order to make the settings work right click on the converter settings click on the compatibility tag and execute on windows 2000 and vuala it works , now you can use the dance mat setting  but in order to use the dance mat settings you must download the newest driver 

[http://www.chinagameware.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml](http://www.chinagameware.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml)

Enjoy if you have any other problem email me, another thing I havent checked the guitar hero controler if it works with this new drivers but with the old ones it didnt work on guitar zero only frets on fire

---

### Post by DarkN00b on 2007-11-13
Well I didn't report back when I said I would, but better late than never I guess. :?

The good news is that this adapter now works perfectly with the current Gutsy kernel - 2.6.22-14 (generic in my case).

I plugged the adapter in, plugged in my PS controller and played a few games to test it. Everything worked fine with _no_ problems whatsoever.

---

### Post by andale on 2008-01-13
...click on the converter settings click on the compatibility tag and execute on windows 2000 and vuala it works.


i'd love to, but...
i plug it in and see nothing, (not a surprise, this ain't windows) but i don't know where to find these things, is there a controller/joystick handler program that i'm unaware of? you'll have to excuse me, i'm still pretty new at this but trying to be ambitious about it.

---

### Post by andale on 2008-01-13
guess noone's gonna notice this, since it was last replied to last november, o well. i should really pay more attention to that date.

---

### Post by pogenwurst on 2008-06-13
For anyone who finds this thread on Google (I did) while having trouble using a Gamecube controller with this adapter -- it's actually an easy issue to sort out, once you realize what's happening. For whatever reason, plugging in this adapter with a Gamecube controller creates two joysticks (in my case js0 and js1). js0 does nothing; js1 works perfectly.

---

