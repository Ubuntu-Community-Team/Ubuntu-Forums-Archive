---
title: "Xbox 360 controller in Hardy?"
date: 2008-06-18
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2008-06-18
I've just a bought a nice cheapo Speedlink Xbox 360 style pad from ver nets, but bugger me if it doesn't work in Hardy. I found a couple of guides, but can't seem to get it going. It's odd, because it turns up in Mupen and whatnot as "ACRUX USB Gamepad 8116", but won't let me set any buttons. I've tried JSCalibrator but it's the same there too. It's in the menu, but not responding.

Has anyone gotten these types of pad to work in Hardy? Do you have an easy-to-follow guide for those of us whose time is limited for playing in Linux? I'd hate to have to install bloody Windows just to use this pad. I'd only be playing the same games there that I would have been playing in Ubuntu anyway, but I don't want to send the pad back because it's very, very nice!

Thanks all.

EDIT: [It's this one.]("http://www.play.com/PC/PCs/-/673/880/-/3507653/Speed-Link-XBOX-360-Style-USB-Gamepad-For-Windows-With-Force-Vibration-Black/Product.html?searchtype=genre") Very well made, but not for Linux - Thus far!

---

### Post by BigSilly on 2008-06-19
Anyone? I followed a guide and got so far, but after compiling the driver with Scons (I think it was), the terminal said I didn't have an Xbox or Xbox360 pad even plugged in!

Halp!

---

### Post by torturedutopian on 2009-08-24
I have exactly the same issue and would be most interested in a solution :) 

I'm pretty sure some ppl did manage to get it working, because I saw it listed here :

[https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done)

Cheers !

---

### Post by torturedutopian on 2009-08-24
Well, it turned out I just had to install the package xserver-xorg-input-joystick AND replug the joystick once the system is loaded !

(BTW, I would be interested in knowing why I have to do so :)

Oh, something else. The gamepad controls the mouse pointer without my wanting it :)

---

### Post by BigSilly on 2009-08-25
Well, look at that, it works! Thanks for the messages you sent to me. I've only just been able to give this a go, and I'm very surprised to find that it works. I've just been playing Gens with it. Thanks for your efforts here torturedutopian! It does seem to control the mouse though. I'll bet there's a way to stop that somehow. Maybe some nice person will pop in soon and tell us how! ;)

Who do we tell to get this put in by default? Be great if it worked without any user intervention.

---

### Post by torturedutopian on 2009-08-25
OK, I found the solution. Or at least, a work-around.

1) install xserver-xorg-input-joystick
2) copy acrux-usb-gamepad-8116.fdi to /etc/hal/fdi/policy (provided here : [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done) )
3) edit this .fdi file so it looks like so :
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
   <match key="input.product" string="ACRUX USB GAMEPAD 8116">
     <remove key="input.x11_driver" />
     <merge key="input.x11_driver" type="string">joystick</merge>
     <merge key="input.x11_options.SendCoreEvents" type="string">false</merge>
   </match>
 </device>
</deviceinfo>

```
4) restart X
5) unplug/replug the controller before using it

I left a bugreport here : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/418470)

Can anyone test with Karmic ?
I really hope none of those steps will be necessary in Karmic. What should I do to help ?

---

### Post by torturedutopian on 2009-08-25
Well, there's still one issue :

the second analog stick seems to control the mouse wheel ! And directions seem to be inverted, somehow (only with the second stick)

(you may test it with "Gunroar" and the "twin sticks" mode :)

---

### Post by benmoran on 2009-08-28
Yeah, the built in xbox 360 controller driver is a bit off. There is another option:  [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

Has anyone tried this yet?

---

### Post by BigSilly on 2009-08-30
Thanks again here for these solutions TorturedUtopian. Absolutely fantastic that I can use this pad in Linux now. And you're a Kenta Cho fan too! Cool! :D

It seems to be working fine, in spite of it still messing about with the mouse. I'm not too bothered about that though. Definitely better than nothing! My thanks again. :)

---

### Post by torturedutopian on 2009-09-14
Hmm, a workaround for the fact that the pad also controls the mouse.

In gnome, run the shortcuts editor (in ubuntu preferences menu). Assign a key combo to the fullscreen toggle switch (not assigned by default). I chose Alt+Enter from the keyboard not to raise a conflict with Alt+Return.

Now, run rrootage, do alt+enter : the 360 pad won't trigger the mouse (because there's no mouse in fullscreen). :)

Edit : well actually, I talked too quickly ;) Hope it'll be really fixed in future ubuntu releases !

---

