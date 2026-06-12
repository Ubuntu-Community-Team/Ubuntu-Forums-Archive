---
title: "Sorry, no sensors were detected."
date: 2011-06-18
forum: Desktop Environments
---

### Post by nrundy on 2011-06-18
I'm trying to setup a Sensors reader on a friends computer so he can see the running temperature. Temperature readouts work fine on his Windows XP installation. But when I install Gnome sensors-applet it says "No sensors found!" and when I run lm-sensors, it says 

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

anybody know how to get Sensors working under ubuntu?

---

### Post by nrundy on 2011-06-18
What app do you guys recommend for a non-gui, simple text display of the system Temperatures?

---

### Post by elliotbeken on 2011-06-18
> sudo apt-get install lm-sensorsthen 

> sudo sensors-detect

answer all with the recommended answer

this should help find the sensors in the system. (it seamed to work for me)

---

### Post by nrundy on 2011-06-19
yeah, this is what I did. Got the message I posted :(

---

