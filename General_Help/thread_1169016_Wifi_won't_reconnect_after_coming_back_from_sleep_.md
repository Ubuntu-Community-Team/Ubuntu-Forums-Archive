---
title: "Wifi won't reconnect after coming back from sleep mode"
date: 2009-05-24
forum: General Help
---

### Post by cody7002002 on 2009-05-24
Pretty much exactly what the title says. I have an Asus eeepc 1000he and whenever I close the laptop then open it back up and come out of sleep mode my wifi won't reconnect. It tries to connect for a while but then says it can't connect

---

### Post by kerry_s on 2009-05-24
you need to unload the modules first.

**gksudo gedit /etc/pm/config.d/config**

put:

**SUSPEND_MODULES="your-wireless-card driver"**

example: i use a usb wireless dongle, the driver is zd1211rw.

---

### Post by cody7002002 on 2009-05-24
how do I find out what my wireless card driver is?

---

### Post by kerry_s on 2009-05-24
> **cody7002002 said:**
> how do I find out what my wireless card driver is?

in a terminal:
**lsmod**

i think it's "ath9k" on the eee's.

**SUSPEND_MODULES="ath9k"**

---

### Post by cody7002002 on 2009-05-24
Awesome, that worked. Thanks guys =)

---

### Post by persapiens on 2010-07-17
I can't find my wireless card driver of my dell inspiron mini 10.
When i run "lsmod" I get the result attached :)

Thanks in advance.

---

### Post by troelsm on 2010-11-26
Hi,

Just wanted to say thanks for this tip. I have a 1000HE too, with the same problem after installing Ubuntu 10.10 just now. Did a quick search and found this. So thanks again.

So now I'm wondering why on earth this isn't default setting?!

Kind regards

---

