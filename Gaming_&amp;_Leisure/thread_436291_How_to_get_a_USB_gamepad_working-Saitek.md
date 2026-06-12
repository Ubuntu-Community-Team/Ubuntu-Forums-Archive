---
title: "How to get a USB gamepad working-Saitek"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by bokorpop on 2007-05-07
I am new to Ubuntu/linux and one important element of my desktop experience is MAME and using my Saitek p990 usb gamepad.

I can't figure out how to get the gamepad working, either in MAME or any other game (Gnometetris, NIbbles etc). I have no idea how to install or test out the gamepad in any way. In windows I would go control panel>gamepads or something like that but I don't know what to do here.  According to some reviewers on amazon, my gamepad works great with linux. What do I do?

---

### Post by beeldings on 2007-05-07
I have the same exact gamepad and it worked out-of-the-box with Ubuntu Feisty. What version of Ubuntu are you using? I never used MAME so I can't really provide support for that program, but what I would suggest to you is to download jscalibrator through the Synaptic Package Manager as well as several joystick-related utilities:
```

sudo apt-get install libjsw2 libjsw-dev joystick jscalibrator

```

I installed these programs prior to connecting my gamepad to my PC and everything worked with zero configuration on my part, except of course I had to set up Cedega to use my gamepad. jscalibrator will allow you to calibrate your gamepad using a nice GTK interface and then save these changes to your home directory. My advice to you is to install the above applications, then plug in your gamepad and then load jscalibrator. If jscalibrator can detect your gamepad, then everything should work. If all else fails, try connecting the gamepad to a different USB port. I'm no expert on the topic, but I hope my experiences can help you.

---

### Post by bokorpop on 2007-05-08
I have Fiesty.
I got the JS calibrator, and it responds to my gampead the way it should, however, I still can'tt get the joystick to work in a game. What games do you use the gamepad with? Maybe I can test to see if it is something specific abouy the games I am trying to play. Can I use the gamepad with any of the games that are installed by defaul in fiesty? Do I have to configure from inside the game? If so, how?

---

### Post by bokorpop on 2007-05-13
hey umm, this still isn't solved. Is there a simple game anyone can recoomend which I can test my gamepad out on.

---

### Post by nowshining on 2007-07-26
hey beeldings :) i your comment helped me at least, unplugged,  - opened up jscalibrator again and this time plugged it in while in that program and it lit up...whew at least one problem is solved and that was DOES IT WORK...now to get it work.. :)

---

### Post by nowshining on 2007-07-26
:( not it will not even lite up...

---

### Post by nowshining on 2007-07-26
and now it does.. :) a bit flaky this time, but after keeping on plugging it in and out if finally works..YAY

---

