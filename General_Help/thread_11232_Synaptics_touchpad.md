---
title: "Synaptics touchpad"
date: 2005-01-14
forum: General Help
---

### Post by st01c on 2005-01-14
How does one enable the touchpad function - the mouse is defined as a synaptics touchpad in the x config.
TIA,
st01c

---

### Post by JohnQ on 2005-01-14
I'm sorry, could you clarify what you mean by "touchpad function."  I don't understand what you mean by that.

---

### Post by st01c on 2005-01-14
Hitting the touchpad for selection is not functioning.  
/st01c

---

### Post by LB06 on 2005-01-15
I think your touchpad is running in PS/2 emulator mode. Are there any errors in your X logs?

---

### Post by feneks on 2005-01-16
have you already done 
```
sudo apt-get install xfree86-driver-synaptics
```
and the configuration as it is written in
/usr/share/doc/xfree86-driver-synaptics/README.Debian

The next step will be to see if your Touchpad is recognized the right way.
What does your dmesg say?

> Synaptics Touchpad, model: 1
 Firmware: 4.1
 Sensor: 8
 new absolute packet format
**input: SynPS/2 Synaptics TouchPad on isa0060/serio2**


It's important that input says SynPS/2 Syanptics ...

---

