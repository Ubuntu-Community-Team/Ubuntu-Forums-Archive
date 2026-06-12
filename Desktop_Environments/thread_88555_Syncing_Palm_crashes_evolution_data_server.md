---
title: "Syncing Palm crashes evolution data server"
date: 2005-11-10
forum: Desktop Environments
---

### Post by fdimmling on 2005-11-10
When I try to sync my Palm Tungsten E with evolution using the pilot-applet it crashes the evolution data server. From the conduits I have only activated calendar (or addresses) "copy from pilot". Which conduit I use or using both does not matter. Sometimes it is working and then everything is copied correctly but on most tries it starts syncing until the crash message appears.

Any help? :confused: 

Friedrich

---

### Post by fdimmling on 2005-11-15
No one syncing a Tungsten E with evolution by gnome-pilot or is everybody except me happy having no problem???:confused:

---

### Post by potrick on 2005-11-18
Hey, I'm syncing with a Tungsten E very happily until a couple days ago. Now I can't start evolution without it crashing. I'm not sure if this is related or not, though.

potrick

---

### Post by Spie on 2005-11-18
I sync a Tungsten E with Evolution too. That error occurs to me too, sometimes. I can't remember when or how, but I thought it helped when I change to ttyUSB1 instead ttyUSB0. I can't remember exactly, I'm not at home now, but I will take a look tomorrow.

---

### Post by fdimmling on 2005-11-18
[QUOTE=Spie]I sync a Tungsten E with Evolution too. That error occurs to me too, sometimes. I can't remember when or how, but I thought it helped when I change to ttyUSB1 instead ttyUSB0. I can't remember exactly, I'm not at home now, but I will take a look tomorrow.[/QUOTE]

I'm using /dev/ttyUSB1. Syncing with JPilot causes no problems as far as I can see. 

Friedrich :confused:

---

### Post by Spie on 2005-11-28
This is what happens on my PC and Palm:
If I connect my Palm and try to sync it, after some time the Palm gives the "can not connect" error.
But if I start System -> Preferences -> PalmOS Devices and press HotSync everything works perfectly.

---

### Post by talishte on 2007-10-04
Try  loading the module

```

sudo modprobe visor
```

---

