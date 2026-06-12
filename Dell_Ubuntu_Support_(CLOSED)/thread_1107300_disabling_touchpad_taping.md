---
title: "disabling touchpad taping"
date: 2009-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-03-26
Kubuntu 8.10, KDE 4.2
I really need to disable that touchpad "click on tap" senseless feature because it's really driving me crazy. I'm just about to put a piece of ductape on it. I tried that "touchfreeze" program that doesn't actually work. Does anyone know how to do it?

---

### Post by anjilslaire on 2009-03-26
Is there not an option in the mouse settings in KControl?

---

### Post by geoffm on 2009-03-27
> **anjilslaire said:**
> Is there not an option in the mouse settings in KControl?

I wish!
There's not kcontrol in KDE 4.2, it's "System Settings"

---

### Post by ugm6hr on 2009-03-28
8.10 doesn't use the xorg.conf synaptic settings for the touchpad, so it is actually harder to turn off than in older versions.

There is a wiki page: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

It appears qsynaptics may help.

Or you could just add to the autostarted apps list:
synclient MaxTapTime=0

---

### Post by geoffm on 2009-03-31
> **ugm6hr said:**
> 8.10 doesn't use the xorg.conf synaptic settings for the touchpad, so it is actually harder to turn off than in older versions.

There is a wiki page: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

It appears qsynaptics may help.

Or you could just add to the autostarted apps list:
synclient MaxTapTime=0

"Can't access shared memory area. SHMConfig disabled?"

---

### Post by ugm6hr on 2009-03-31
> **geoffm said:**
> "Can't access shared memory area. SHMConfig disabled?"

[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

---

