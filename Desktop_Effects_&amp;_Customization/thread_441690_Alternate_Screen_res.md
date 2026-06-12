---
title: "Alternate Screen res"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by hammedhaaret on 2007-05-12
Hi.
I finally desided to install fiesty on my laptop.
my screen is 15.4" and can go to 1280x800 which makes Ubuntu look like it is being displayed on a screen several sized to small.

so im currently running it in 1024x768.
but that makes it look just a bit too streched.

so i just want to know if's possible to get a res in between, and how?

hope someone can help me
hammedhaaret

---

### Post by sharke on 2007-05-12
> **hammedhaaret said:**
> Hi.
I finally desided to install fiesty on my laptop.
my screen is 15.4" and can go to 1280x800 which makes Ubuntu look like it is being displayed on a screen several sized to small.

so im currently running it in 1024x768.
but that makes it look just a bit too streched.

so i just want to know if's possible to get a res in between, and how?

hope someone can help me
hammedhaaret
What do you mean by several sizes to small .
regards
Sharke

---

### Post by hammedhaaret on 2007-05-12
i mean like the res is wider than the screen and therefore everything gets squeezed together...

did i make myself clearer?
don't really know how else to put it

hammedhaaret

---

### Post by sharke on 2007-05-12
Now i understand .
Please let us know what graphics you have if intel try installing 915resolution and you will find info in /usr/share doc/915resolution on howto use.
Regards
sharke

---

### Post by hammedhaaret on 2007-05-12
i have a nVidia geforce go 7600 gt with 512 mb of ram

---

### Post by BloodCROSS on 2007-05-13
i have the same problem

My graphic card is ATI Mobility Radeon 9000

after some googling i fixed the problem with

sudo dpkg-reconfigure xserver-xorg

and used autodetect, i don't get it why it couldn't detect that right when installing

---

### Post by hammedhaaret on 2007-05-13
but it detects my gfx card without problems... 
i just want to know wether its possible, and how to get a resolution at, let's say 1124x800
or somewhere else between 1280x800 and 1024x768...

---

### Post by screaminj3sus on 2007-05-13
You can use```
sudo nvidia-settings
``` if you are using the proprietary drivers.

---

