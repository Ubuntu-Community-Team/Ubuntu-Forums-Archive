---
title: "Palm Vx (Serial) does not work"
date: 2005-07-05
forum: Desktop Environments
---

### Post by Shambler on 2005-07-05
Hello,

I'm trying to get my Palm Vx over /dev/ttyS0 running, but with no success. Configuring the Palm with the built-in Gnome application and pushing the Hotsync-button seems not to work...

Any ideas?

---

### Post by Shambler on 2005-07-06
*bump*

---

### Post by the slayer on 2006-08-10
I think u have to enter this "ln -s /dev/ttyS0 /dev/pilot" in the terminal. And then enter this "chmod 666 /dev/ttyS0" Dont forget the "sudo"
It works here.

---

### Post by moon2js on 2006-12-28
I have the same problem with a serial cradle and an older Palm.

> **the slayer said:**
> I think u have to enter this "ln -s /dev/ttyS0 /dev/pilot" in the terminal. And then enter this "chmod 666 /dev/ttyS0" Dont forget the "sudo"
It works here.

Tried that and no such luck.

Basically, I hit the hotsync button and the palm pilot times out waiting for gnome-pilot (or Evolution) to connect.

---

