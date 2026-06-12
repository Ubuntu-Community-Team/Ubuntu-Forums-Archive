---
title: "Multiple mice device and a laptop"
date: 2006-01-01
forum: General Help
---

### Post by viestituote on 2006-01-01
Hello. I have a Fujitsu Siemens laptop running Kubuntu 5.10. I have three mice devices, the Synaptics Touchpad thing that works all right, then a regular Logitech USB scroll wheel mouse and a Wacom Volito tablet (usb).

When I first installed, logitech mouse worked just like it should have, but the tablet didn't get configured properly. I did like people on this forum many times instructed, edited xorg.conf a bit, adding those "stylus" and "cursor" inputdevices at event3. The tablet started to work and even got pressure sensitivity in GIMP.

To find that the tablet was at event3 I had to xxd the /dev/input/ entries.

The problem is that as I use a laptop, I don't keep the mouse and the tablet all the time plugged in, and not every time in the same ports (I have them on both sides of the laptop and I plug them in where needed), so the device name may vary (event3 > event4 and mouse0> mouse1 etc.) quite randomly between boots.

So far, when I had needed to draw something in GIMP, I have gone to /dev/input in console, done ls and manually checked which device points to my tablet by doing a series of xxd commands and then edited xorg.conf's stylus and cursor inputdevices to point at that, and then restarted X. With the logitech mouse I could've done the same but I don't even bother anymore as I can do with the touchpad.

My question is, is there any way I can make the xorg.conf always be aware of those two devices when I boot up, even if I've changed the wires around? Back in Windows it was a lot easier with the mice working right away when I plugged them in.

---

### Post by encompass on 2006-01-01
Well I would have to say first off, that windows never even looks at devices when the USB ports change.  So if you boot with the Mouse in a wrong plug it won't see it.  If at all.  Sound's like you want the features of udev.  I would google udev and learn about that for a while.  I wish I know how to do it.  I am not a pro at udev at all.

---

### Post by cylon359 on 2006-01-01
For the mice, you just use /dev/input/mice instead of the individual mouse entries... not sure about the tablet though.

---

### Post by viestituote on 2006-01-01
Cyclon: There is something about that wacom tablet that makes using mice not favourable. It works ok like that but I can't get pressure support.

Encompass: Thank you, this is quite much what I needed to know. I googled udev as you said and got [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html). With that and man udev I was able to pretty much make it work.

I am currently using what Cyclon suggested, having mice as the main mouse, now need to find a way around that so I can get that pressure in GIMP.

Thanks.

---

### Post by iand675@gmail.com on 2006-01-01
erm.. well I don't have a complete workaround for this, but I suggest writing a shell script and setting it to run on boot. or get some scotch tape and label which device to plug in where:p

---

### Post by encompass on 2006-01-01
Good!  I am glad it is starting to work better... I would highly seggest writing a howto on this subject.  It is important to get those little kinks out of linux systems.  Yummy, I think I want to get a wacom tablet too... they sound cool.

---

### Post by mikeRimex on 2008-07-24
Here is what you want I think

[http://wearables.unisa.edu.au/mpx/?q=mpx](http://wearables.unisa.edu.au/mpx/?q=mpx)

---

