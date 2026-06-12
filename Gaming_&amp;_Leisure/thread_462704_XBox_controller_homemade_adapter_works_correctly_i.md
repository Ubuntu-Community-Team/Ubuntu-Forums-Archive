---
title: "XBox controller homemade adapter works correctly in Feisty?"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by DARKGuy on 2007-06-03
Hey :)

I'm about to spend some money in an XBox controller so I can use it with Linux games/emulators/beryl/your cat/the fridge/etc. and some Windows games (Halo, NFSMW & such).

I know it works in Windows awesomely, but is it the same for Ubuntu? is there any module/driver for Feisty kernel 2.6.20-16-generic ? does the rumble function works? I'm gonna try these HowTo in case anyone's wondering how to make one:

[http://www.fury-tech.com/en/Guides/Xbox-Controller-PC-Conversion-Mod](http://www.fury-tech.com/en/Guides/Xbox-Controller-PC-Conversion-Mod) <- especially this one
[http://www.llamma.com/xbox/Mods/xbox_controller_to_pc_usb.htm](http://www.llamma.com/xbox/Mods/xbox_controller_to_pc_usb.htm)
[http://xbox-scene.org/articles/xbox-usb-xbox-cable.php](http://xbox-scene.org/articles/xbox-usb-xbox-cable.php) <- and this one
[http://www.ocmodshop.com/ocmodshop.aspx?a=223](http://www.ocmodshop.com/ocmodshop.aspx?a=223)

Can anybody confirm me if they work with all their functions?

---

### Post by DARKGuy on 2007-06-03
Huh, sorry to bump but... nobody? :(

---

### Post by a12ctic on 2007-06-03
[http://www.xbox-scene.com/articles/controller-linux.php](http://www.xbox-scene.com/articles/controller-linux.php)

---

### Post by DARKGuy on 2007-06-03
> **a12ctic said:**
> [http://www.xbox-scene.com/articles/controller-linux.php](http://www.xbox-scene.com/articles/controller-linux.php)

Hey. that helped! actually all I had to do was:

> sudo apt-get install xpad

And for activating it:

> sudo modprobe xpad
sudo modprobe joydev

And it worked! ^_^...

Now, how to test the rumble/vibration function? :(

**Edit:** I just tested it in Windows. It works perfectly. But I don't know how to test it under Linux. Any idea?

---

### Post by po0f on 2007-06-04
DARKGuy,

You didn't have to install [xpad](http://packages.ubuntu.com/feisty/x11/xpad) from the repos to get your Xbox controller working.  If you click on that link and read the description, you'll find it has very little do do with controllers.  ;)

The vanilla Xbox controller works out-of-the-box with stock Ubuntu kernels.  As for testing it, open up a terminal and run this command (^C to quit):

```
$ cat /dev/input/js0
```

If you see a bunch of gibberish scroll by in the terminal, it's working.  :)

Oh yeah, and AFAIK, no rumble.

[EDIT]

Just realized you meant testing the *rumble*, not the controller itself.

---

### Post by DARKGuy on 2007-06-04
> **po0f said:**
> DARKGuy,

You didn't have to install [xpad](http://packages.ubuntu.com/feisty/x11/xpad) from the repos to get your Xbox controller working.  If you click on that link and read the description, you'll find it has very little do do with controllers.  ;)

The vanilla Xbox controller works out-of-the-box with stock Ubuntu kernels.  As for testing it, open up a terminal and run this command (^C to quit):

```
$ cat /dev/input/js0
```

If you see a bunch of gibberish scroll by in the terminal, it's working.  :)

Oh yeah, and AFAIK, no rumble.

[EDIT]

Just realized you meant testing the *rumble*, not the controller itself.

Duh, I didn't know xpad was that, lol xD.... thanks for the tip :) though I was actually testing it with "jstest /dev/input/js0" ;) I didn't know that other way, thanks :).

Hmm, is there a way to enable rumble? or how to activate it? do you know where is xpad's latest source? I haven't been able to find it yet :(

---

### Post by po0f on 2007-06-05
DARKGuy,

I don't think *any* controller under Linux supports force-feedback, sorry.

---

