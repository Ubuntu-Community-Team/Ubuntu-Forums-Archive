---
title: "Show Temp in Panel Applet"
date: 2011-02-11
forum: Desktop Environments
---

### Post by kalsan on 2011-02-11
Hi everybody

There is a little application for the GNOME Panel that shows processor, HDD, RAM, Network etc.
Is there any that shows the current temperature of the Laptop / Computer?
Ubuntu 10.10

Thx
Kalsan

---

### Post by Frogs Hair on 2011-02-11
```
sudo apt-get install lm-sensors
```
```
sudo apt-get install sensors-applet
```

Right click the top panel > add to panel > add hardware sensors monitor. you can change the look by right clicking one of the icons and using preferences. Welcome to forums , by the way.

---

### Post by JC Cheloven on 2011-02-11
> **kalsan said:**
> There is a little application for the GNOME Panel that shows processor, HDD, RAM, Network etc.

For this part of your question, you can simply right-click on the panel, click "add to panel", and choose "system monitor". 

A cpu graph will appear in your panel. Right-click on that. Click "preferences", and mark the boxes you want: there are processor*, ram*, net*, swap, system load, and hard disk*. The asterisks are the ones I like to have at sight (may serve as a suggestion for you). 

Cheers
EDIT: oops, it wasn't a question but a statment. Sorry, I misunderstood :/

---

### Post by kalsan on 2011-02-12
Thank you for your information. I've already had CPU, RAM, Net and HDD on my panel.
There is about 10 values (temp1, FDTZ and much more). Except for the HDD temp, I have no idea what all that means. The temp range goes from 20 to 42°C.
What do all those labels mean?
Thx
Kalsan

---

### Post by Frogs Hair on 2011-02-12
For finding HDD temp , System > Administration > Disk Utility Hard Drive > Smart Data. With out knowing the  operating temp limits of your hardware it is difficult to say what's hot and what's not.

I built my computer , so some of the  information  came with my hardware and some I found  at manufactures website. Running , sensors in the terminal will show high and low temp limits for some components..

---

