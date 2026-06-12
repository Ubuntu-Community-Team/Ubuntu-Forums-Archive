---
title: "Control-Alt-Backspace"
date: 2009-06-01
forum: General Help
---

### Post by UncleMonty on 2009-06-01
Control alt backspace doesn't seem to work since I updated to Jaunty. How do I rectify this?

---

### Post by MichaelSammels on 2009-06-01
I am also having the same problem as well. In order to fix this I manually log out/in again.

---

### Post by m_duck on 2009-06-01
Two solutions [here](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html).

---

### Post by fooman on 2009-06-01
open a terminal (applications > accessories > terminal) and type or copy/paste these 2 commands one at a time,  pressing enter after each one:

```
sudo apt-get install dontzap
``````
sudo dontzap --disable
```  alt-ctrl-backspace should be working again.

---

### Post by MichaelSammels on 2009-06-01
Thanks :) This'll be handy when GNOME freezes :P

---

### Post by colau on 2009-06-01
> **fooman said:**
> open a terminal (applications > accessories > terminal) and type or copy/paste these 2 commands one at a time,  pressing enter after each one:

```
sudo apt-get install dontzap
``````
sudo dontzap --disable
```  alt-ctrl-backspace should be working again.
+1

---

### Post by pastalavista on 2009-06-01
The new way to reboot safely is kinda complex but just in case the dontzap app gets frozen too press these keys in this order: 

While holding ALT+PrintScreen press R,S,E,I,N,U,B one at a time. The way to remember the right sequence (given in the tutorial I read) is Raising Skinny Elephants Is Never Utterly Boring. The devs obviously have a sick sense of humor...

---

### Post by raymondh on 2009-06-01
there's also RT ALT + CTRL + SYSREQ (if you have that key)

Regards,

---

