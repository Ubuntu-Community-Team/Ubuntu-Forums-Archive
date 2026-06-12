---
title: "Original Xbox controller drivers for Gusty"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by NoSmokingBandit on 2007-10-27
I finally got everything working right (yay!) and i was noodling around the games in add/remove programs and installed open arena. I must say that game is amazing and runs smooth on my old crappy pc. Nonetheless, i have an xbox controller i soldiered a usb male end to so i could play halo pc with it. It works great in winxp, but lags a bit in gusty and the triggers dont work as well as the right analog stick only works up/down. All the threads i found here only apply to the 360 controller or are way old. I got jscalibrator, but i dont really think that did anything. The xpad drivers dont seem to work, i cant run ./usbtree it just puts out:
```

steven@steven-desktop:~$ cd Desktop/xpad
steven@steven-desktop:~/Desktop/xpad$ sudo ./usbtree
[sudo] password for steven:
./usbtree: cannot open '/proc/bus/usb/devices'
steven@steven-desktop:~/Desktop/xpad$ 

```

---

### Post by disturbedite on 2007-10-27
ok this is much more simple than you realize with *ubuntu.
i have an original xbox controller s too.  i just plug it in to my converter hub and it works right away.
you don't need any drivers for it cuz the kernel shipped with *ubuntu has the xbox controller driver module built in.
i didn't even have to install any joystick programs.

---

### Post by NoSmokingBandit on 2007-10-27
So i should get rid of jscalibrator and try it again? Ill do that and see what happens. Thanks!

Edit:
jscalibrator has it all fooked, now it works great. That was incredibly easy. Thanks alot man!

---

### Post by disturbedite on 2007-10-27
yeah, i was a bit surprised about how easy it was too.

---

### Post by Ferrat on 2007-11-09
Hmm ok I've been trying to get my old xbox control to work, it shows up with lsusb but just can't get it to do anything??

Never mind, a lose wire ^^ fixed

---

### Post by NoSmokingBandit on 2007-11-09
got to be careful with that soldier there boy.. :guitar:

---

### Post by Ferrat on 2007-11-09
Hehe
BTW, is there any way to get to use the gamepad in games/apps that normaly don't use it? 
For ex. my Loki version of Rune would be fun to get gamepad stearing on and some other games like Guild Wars in Wine ^^
Guild Wars and Rune should work if I just can get them to register it's input correctly since the gamepad har more buttons than either game really use?

---

### Post by NoSmokingBandit on 2007-11-09
Im sure there is a way to do it (this is linux, everything is possible) but it may take some work. I only ever used mine in Open Arena and Sauerbraten in which it worked right away. Maybe if you could convice the game that the controller is a keyboard and map keys to gamepad buttons you could do it. I dont know how that should be done, but it sounds plausible.

---

### Post by disturbedite on 2007-11-09
oh sweet, it works in openarena?  i hadn't tried it yet with openarena...

---

### Post by NoSmokingBandit on 2007-11-09
it works perfect in OA, just make sure you set the buttons to your preference in the options menu.

---

### Post by Ferrat on 2007-11-10
> **disturbedite said:**
> oh sweet, it works in openarena?  i hadn't tried it yet with openarena...

Works flawless in OA and so far in all emulators I've tried, just need to get it to work as a "keyboard+mouse" in other games and I'm very happy :) 
Would be great to plau Guild Wars with a gamepad :)

---

### Post by Ferrat on 2007-11-11
No one knows how to get a gamepad to register as a hid and get it to work as a mouse ect binding keyboards keys to the buttons? 

Found a program that does it in Windows but no linux counterpart?

---

### Post by Tarmael on 2007-11-22
Shouldn't you just be able to edit the xorg.conf file?

Add it there, add device mapping to the controller and register it all there as a keyboard?

But keeping that in mind you'd probably have to have a program that allows you to change where the maps are for that particular module.

Eh, complicated, I'm getting some coding ideas here and there for a new gui or cli to do all that, but I don't know enough about coding nor the hardware side about it to make to project myself.

---

### Post by markyb86 on 2007-12-11
OH THIS IS AMAZING!! I have 2 adapters i created using the dongles and spare usb cables and they stopped working in vista, so then i go the commercial route which works for a little bit and also stops working alltogether. Ubuntu being plug and play with the controller is the most amazing thing i have ever seen!!!!!

---

### Post by disturbedite on 2007-12-11
as i said, it isn't ubuntu exactly, its the kernel, not the OS that has them built-in.

---

### Post by The Steve-O on 2008-08-05
Does Hardy Heron work with the xbox controllers?

---

