---
title: "Load bt878 module on boot?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by hraposo on 2006-08-31
How can I do to ubuntu load bt878 module on boot?

---

### Post by angkor on 2006-08-31
after confirming the modules works when you start it manually, you can put the name of the module in /etc/modules

```
gksudo gedit /etc/modules
``` and add the name at the bottom of the file.

Hope this works, I've done it succesfully with the snd_bt_sco module (for my bluetooth headset).

---

### Post by hraposo on 2006-08-31
I solved the problem of load bt878 on boot. I put bt878 in /etc/modules.
My problem now is when I start TVtime appears the message:> No such file or directory /dev/vide0This means that ubuntu don't recognizes my usb tv-card. What can I do now?

---

### Post by Colonel Kilkenny on 2006-08-31
This "No such file or directory /dev/vide0" should talk about video0 not vide0, but I guess it was just typo from you.

I'm not an expert but I had to do "sudo modprobe bttv tuner=x" with my tv-card to get it working.
The list of tuners and their numbers (instead of x) is somewhere in your computer and probably also in web.

edit. And perhaps you should say your cards manufacturer and other information so someone with similar card could help.

---

### Post by hraposo on 2006-08-31
> sudo modprobe bttv tuner=x" 
How can you find the number of x

---

### Post by mjziegle on 2006-08-31
> **hraposo said:**
> How can you find the number of x

[http://www.tldp.org/HOWTO/BTTV/modprobe.html](http://www.tldp.org/HOWTO/BTTV/modprobe.html)

---

### Post by hraposo on 2006-08-31
thank's

---

