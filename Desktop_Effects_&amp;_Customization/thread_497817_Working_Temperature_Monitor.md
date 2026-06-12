---
title: "Working Temperature Monitor"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by `danny on 2007-07-10
I just installed linux yesterday and I have tried multiple sys temp monitor like Gkrellm with no success. My hardware is pretty new (e6600, ASUS P5K Deluxe, 2x1DDR2 800 Ballistix, evga 8800GTS) so I am guessing there might be some compatibility issues with the sensor modules and my motherboard? Any suggestions on getting some sort of temp monitor to work on my install of ubuntu?

---

### Post by dabl on 2007-07-10
Use Synaptic to install lm-sensors.

Once the package is installed, you have to open a console and enter ```
sensors-detect
``` (can't remember if you need "sudo" that or not, sorry).  It will run you through a script -- just accept defaults.

Then, there is a sensor display package - I think it is "xsensors" that will show the sensor values.

Also, if you want to get fancy, there are a zillion superkaramba "themes" with sensor outputs. :popcorn:

---

### Post by quokka on 2007-07-10
See my posts about getting lm_sensors ro work on Asus P5K towards the end of this thread:

[http://ubuntuforums.org/showthread.php?t=484189&highlight=p5k](http://ubuntuforums.org/showthread.php?t=484189&highlight=p5k)

---

### Post by `danny on 2007-07-10
> **dabl said:**
> Use Synaptic to install lm-sensors.

Once the package is installed, you have to open a console and enter ```
sensors-detect
``` (can't remember if you need "sudo" that or not, sorry).  It will run you through a script -- just accept defaults.

Then, there is a sensor display package - I think it is "xsensors" that will show the sensor values.

Also, if you want to get fancy, there are a zillion superkaramba "themes" with sensor outputs. :popcorn:

Yea when I load xsensors I just get this tiny little window on my desktop that doesn't display anything and I looked at the solution quokka showed but I don't really get what I am doing...

---

### Post by jjross on 2007-07-10
Try this How To, it worked for me
[https://help.ubuntu.com/community/SensorInstallHowto]("https://help.ubuntu.com/community/SensorInstallHowto")

---

### Post by reacocard on 2007-07-10
Um, what about this: [http://www.getdeb.net/app.php?name=CompTemp+Monitor](http://www.getdeb.net/app.php?name=CompTemp+Monitor)

It's a simple deb, and you just add the applet to the panel, no extra config needed.

---

### Post by `danny on 2007-07-11
> **reacocard said:**
> Um, what about this: [http://www.getdeb.net/app.php?name=CompTemp+Monitor](http://www.getdeb.net/app.php?name=CompTemp+Monitor)

It's a simple deb, and you just add the applet to the panel, no extra config needed.
Already tried that, didn't work

---

### Post by quokka on 2007-07-11
> **`danny said:**
> Already tried that, didn't work

Did you read the thread I linked to above ? As I understand it you need kernel >= 2.6.21 and the latest lm_sensors.

---

### Post by `danny on 2007-07-11
> **quokka said:**
> Did you read the thread I linked to above ? As I understand it you need kernel >= 2.6.21 and the latest lm_sensors.

Well I couldn't really find a way to compile the kernel the "ubuntu way"

---

### Post by quokka on 2007-07-12
> **`danny said:**
> Well I couldn't really find a way to compile the kernel the "ubuntu way"

[http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

---

