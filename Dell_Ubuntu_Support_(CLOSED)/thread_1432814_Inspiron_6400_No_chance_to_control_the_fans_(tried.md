---
title: "Inspiron 6400: No chance to control the fans? (tried pwmconfig and i8kutils)"
date: 2010-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pifilatakanemu on 2010-03-18
Hey there, my Inspiron 6400 is quite noisy as the fans hardly stop to work.
I already spent some hours in order to find a solution.

It does not work with **pwmconfig**:

> /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

and **i8k **does not work either, in contrary: the fans start blowing for a couple of seconds, then they stop for a second and start again.

Any suggestions?

---

### Post by grandsatrap on 2010-03-22
I am also having trouble with i8k on my Inspiron 1501. 
There is no fan control nor fan readouts. My fans want to keep running until the temperature is down to 37C.


Conky says that i8k is disabled. I have no idea how to enable it.

Output of i8kctl:
1.0 (null) xxxxxx -1 -1 -1 -1 -1 -1 -1

---

### Post by cnbiz850 on 2010-09-11
I am really annoyed by this problem.  My post is [here]("http://guide.ubuntuforums.org/showthread.php?t=1547952").  Have you found a solution?

---

### Post by tunist on 2010-10-29
not that it helps you, but i am also finding no way to get the fanspeed to be changeable.

someway along the process i did manage to disable the fan completely.. which would be a major pain.. except that i have a cooler base that the laptop sits on so its actually fine..
(the cooler base fan is more effective at cooling the laptop than the default system fan is).

still, i'm looking for a tool to get the fanspeed to change.

---

### Post by bobmartens on 2010-11-01
I have an Inspiron 6000. No fan speed control in latest Bios. The only option to mufflet it a bit is a setting for hdd, to set it quieter, but possilby slowing performance a little. Also be sure no unnecessary cd's are in the dr-rom drive. Mine tends to speed up without reason to helicopter liftoff sound emulation. When using cpu eating programs I put two (equal sized) novels under each side to enhance airflow. Really makes a difference.

---

### Post by Captain Tacos on 2010-11-14
Ah! so there's no hope for us on Inspirons then?
I've spent the whole afternoon searching how to slow down my roaring fans and finally I've made it here.

I have an Inspiron E1705 and I guess I'll just have to get used to the noise, eh.

---

### Post by tunist on 2010-11-14
i just got the fan working on my inspiron 6400..
i updated (fresh install) to unbuntu 10.10.

then looked in the software center and installed i8kutils.
that in itself did nothing in terms of activating a monitor or fan speed control.

however, i then entered via the terminal:


sudo service i8kmon start

which informed me that the service needed to be activated by editing a file: 

sudo gedit /etc/default/i8kmon

and set 'enabled = 0' to 'enabled = 1'

then i entered

sudo service i8kmon start
i8kmon

and bingo..
a tiny popup tab that shows the temperature and a button that switches between 'fan off, fan low and fan high'.

;)

---

### Post by AaronD12 on 2012-06-10
My Inspiron 6000 thanks you. I did notice I had to install the Tk toolkit for Tcl and X11 (runtime files). 

What appears is a tiny window with two boxes inside: The top one shows the temperature in degrees C and the bottom one toggles (on click) between blank (fan off), 1 (fan on slowly), and 2 (hurricane-force winds).

---

