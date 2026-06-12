---
title: "Screen fills with letter E"
date: 2009-01-26
forum: General Help
---

### Post by linuxisevolution on 2009-01-26
I just put in a new graphics card into my sisters system. Actually, it was a new motherboard, graphics card, and ram. Now, when shutting down, it will just say "powering off". And I have to press the power button to do so. During reboot, her screen filled with a million letter "E"'s with little apostrophes over them. . .. WTF?
Specs before upgrade:
Pentium 3 1ghz
348mb ram sd-pc-133
Intel i810 8mb

After:
Pentium 3 1.23ghz
256mb DDR 226 ram
Nvidia Geforce MX4000

So what's the problem? Thanks!

---

### Post by abn91c on 2009-01-26
try a different screen refresh rate

---

### Post by linuxisevolution on 2009-01-26
> **abn91c said:**
> try a different screen refresh rate

Tried it. It hasn't happened again. I installed the nvidia-glx drivers, but when I launch a game like bzflag I get Couldn't find matching glx visual.

---

### Post by malfist on 2009-01-26
Use envyng to install the video drivers unless you know how to do it manually. It can be very tricky to do it manually. I just updated to the new 180.22 drivers and had hell for about an hour until I made it work. Envy will install slightly older drivers but they are still good.

---

### Post by linuxisevolution on 2009-01-26
> **malfist said:**
> Use envyng to install the video drivers unless you know how to do it manually. It can be very tricky to do it manually. I just updated to the new 180.22 drivers and had hell for about an hour until I made it work. Envy will install slightly older drivers but they are still good.

I still get glx visual not found :(

---

### Post by malfist on 2009-01-26
How was you originally trying to install the driver?

---

### Post by linuxisevolution on 2009-01-26
> **malfist said:**
> How was you originally trying to install the driver?

By the system >> administeration >> restricted drivers . I checked the nvidia box and rebooted. Then I unistalled the drivers with envyng and installed the envyng drivers. Now I get "Low graphics mode" before Fluxbox starts :(

---

### Post by linuxisevolution on 2009-02-03
I fixed it. Simply removed the drivers and now everything works. No direct rendering but the games play smoothly.

---

