---
title: "Grand Prix Legends"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by phoogkamer on 2008-06-13
Hello,

Does anyone have any experience with Grand Prix Legends 2004 running on Ubuntu??
I am able to install with wine, but after that it crashes or runs very, very slowly :(

Peter

---

### Post by Joeb454 on 2008-06-13
Check the [Wine AppDB]("http://appdb.winehq.org") and see if the game is on there :)

---

### Post by phoogkamer on 2008-06-13
The application is there and should work flawlessly.

---

### Post by Tomatz on 2008-06-13
> **phoogkamer said:**
> The application is there and should work flawlessly.

What version of wine was it tested on and what version do you have installed?

---

### Post by phoogkamer on 2008-06-13
I am running wine version 0.9.59-0ubuntu5 and GPL was tested on version 0.9.30.
I am trying to get some debug info about wine running GPL. Could you tell how I can get some results with debugging?

Peter

---

### Post by Tomatz on 2008-06-13
What is the spec of your pc?

---

### Post by phoogkamer on 2008-06-13
I have a Dell Dimension 3100, Intel Pentium 4 1.6 Ghz processor, nvidia 6200 graphics card. Kernel version 2.6.24-18.
If you want to know more, just ask.

Peter

---

### Post by phoogkamer on 2008-06-13
For controls I have a Logitech Force Feedback EX with pedals.

Peter

---

### Post by Tomatz on 2008-06-13
> **phoogkamer said:**
> I have a Dell Dimension 3100, Intel Pentium 4 1.6 Ghz processor, nvidia 6200 graphics card. Kernel version 2.6.24-18.
If you want to know more, just ask.

Peter

If compiz is on you will need switch it off when playing 3d games.

To turn it off temporally type this in a terminal:

```
metacity --replace
```

Then try the game again ;)

---

### Post by phoogkamer on 2008-06-13
Ok, that helped a lot. Thanks. After that I noticed that my 3d accelerator wat still at 3directX7d or something like that. So I switched to OpenGL en now it works at normal speed. Do you have any knowledge about configuring Logitech racing wheels on linux? I can get the steering and pedals to work, but not the shifting up and down buttons at the back of the steeringwheel.
Also the sound is crapy. Could this have something to do with wine? Sound on Ubuntu itself is perfect.

Peter

---

### Post by Tomatz on 2008-06-13
> **phoogkamer said:**
> Ok, that helped a lot. Thanks. After that I noticed that my 3d accelerator wat still at 3directX7d or something like that. So I switched to OpenGL en now it works at normal speed. Do you have any knowledge about configuring Logitech racing wheels on linux? I can get the steering and pedals to work, but not the shifting up and down buttons at the back of the steeringwheel.
Also the sound is crapy. Could this have something to do with wine? Sound on Ubuntu itself is perfect.

Peter


Goto *[COLOR="Blue"]applications, wine, configure wine[/COLOR]* then click the **[COLOR="Blue"]audio[/COLOR]** tab (in wine config). Then try changing the (audio) hardware acceleration via the dropdown box to basic (you can try standard just find which works best). That usually helps with choppy audio in wine.

As to the steering wheel, i dont know if you will get all the buttons working. Especially as the game is being run through wine. You could try googling but i doubt you will fix this.

Hope that helps ;)

---

### Post by phoogkamer on 2008-07-08
Thanks for all the help. I am able to start GPL now and configure my steering wheel, but when I start the game it does not run flawlessly. It goes from frame to frame and is very slow and unresponsive. I have switched to OpenGL and adjusted the screen resolution to the same size as the wine virtualization. Disabled a lot of track objects and lowered the "Detail bias". Could this be a problem with the setup of my video card??

Peter

---

### Post by phoogkamer on 2008-07-10
Ok, I have got it working perfectly now. Came across the original version of GPL on a second hand store and thought it would be nice to have the original one. Installed it with the GPL installer and got GPL to use the OpenGL 3d driver. Now it runs ok. I just want to figure out if I can get the other buttons on the logitech wheel to work. This will be a nice challenge.

Peter

---

