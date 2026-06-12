---
title: "Anyway to configure PS3 wireless controller in 13.04"
date: 2013-05-05
forum: Gaming &amp; Leisure
---

### Post by fazillatheef on 2013-05-05
Installing Qtsixa just disables the normal bluetooth. And the joystick doesn't work. Any link or tutorial to set it up would be helpful.

With the usb connection nothing needs to be configured. It just works.

---

### Post by Ranko Kohime on 2013-05-08
I haven't figured that out, myself, but I have gotten the PS3 controller to work using sixad, which is the backend that Qtsixa uses.

Type "sudo sixad -s" into a terminal, and then press the PS button.

If it still doesn't connect, you may need to pair it, by plugging the controller in, then running "sudo sixpair".  Both sixpair and sixad should be included in the Qtsixa package.

---

### Post by nsync on 2013-05-11
i once used a ps3 controller for playing minecraft.. i configured it on windows .. you could download/install wine, then download Ds3 tool here

32bit - [http://mediafire.com/?d60y8do4drdse2u](http://mediafire.com/?d60y8do4drdse2u)
63bit - [http://mediafire.com/?k80b5m93gh7icak](http://mediafire.com/?k80b5m93gh7icak)

just plug your controller and run ds3 tool.you can also configure the keys the way you wish ;D
if you need tutorials just google it.. 
its been years since i used ds3 but it still works.. its easy as 678.

---

