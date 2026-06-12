---
title: "Bluetooth Dell Mini 9 Ubuntu 8.10"
date: 2009-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bigee1212 on 2009-02-17
hey all, 
i want to connect my moto q to my mini 9 ( for obex transfers). i have ubuntu 8.10, and when i try to search for devices with my laptop, nothing shows up. i cant use the FN key to turn on bluetooth because it doesnt work with 8.10, but i got Aircraft manager and i can turn on bluetooth using that. 

when i search for devices with my phone, i can find 3-4 devices (college campus) but not my laptop. My laptop, however, doesnt see any device including what my moto Q sees as well as the Q itself. any ideas ?

---

### Post by dzark on 2009-02-17
Have you installed any of the 'bluez-' packages? Open System->Admin->Synaptic and search for 'bluez'. If you select bluez-gnome it should bring most of the rest with it.

---

### Post by bigee1212 on 2009-02-17
i tried re installing the "bluez" package via synaptic. no go. 

but something to note, when i first removed Bluez, the bluetooth icon in the tray was still there. it still let me right click it and "setup new device". i dunno it didnt find anything with the bluez un installed' after i re installed, i have the same problem. it cant find anything.

is there some command i can run in the terminal to verify if the bluetooth adapter works.?

---

### Post by dzark on 2009-02-17
> **bigee1212 said:**
> i tried re installing the "bluez" package via synaptic. no go. 

? What does that mean? It wont install? It has installed but doesn't work?


> **bigee1212 said:**
> is there some command i can run in the terminal to verify if the bluetooth adapter works.?

try lspci or lsusb 

You have 'Airplane Mode' installed. And bluetooth enabled under that?

---

