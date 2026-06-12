---
title: "Color depth"
date: 2005-09-29
forum: Desktop Environments
---

### Post by cwu on 2005-09-29
So this is probably a very stupid question but, where can I change the color depth for my machine? It's at 24 bits and the desktop background isn't very smooth.

---

### Post by Alexander Kirillov on 2005-09-30
[QUOTE=cwu]So this is probably a very stupid question but, where can I change the color depth for my machine? It's at 24 bits and the desktop background isn't very smooth.[/QUOTE]

You can manually edit file /etc/X11/xorg.conf
(make sure you make a backup first!). You must use sudo to do it, e.g. 
sudo nano /etc/X11/xorg.conf 
Look for 
Section "Screen"
and change the value of "DefaultDepth"

---

### Post by eduard0 on 2005-09-30
Am I totally wrong if I say that there isn't considerable difference between 24 bit colors and 32 bits? And I think that I've read somewhere that 32 bit colors aren't really 32 bits, instead of that they would be somehow extended 24 bits, am I wrong?

---

### Post by cwu on 2005-09-30
I'm not really the best person to ask for that. I don't know if it'll make a difference. I just want the odd aura effect to go away. Basically, in the background pic the as the gradient changes it does so non-smoothly. So there are "bands" or color rather than smooth changes.

Again, this is really inane so I almost feel bad sullying the forums with such a stupid and superficial question.

---

### Post by darkmatter on 2005-09-30
[QUOTE=eduard0]Am I totally wrong if I say that there isn't considerable difference between 24 bit colors and 32 bits? And I think that I've read somewhere that 32 bit colors aren't really 32 bits, instead of that they would be somehow extended 24 bits, am I wrong?[/QUOTE]

Though a very basic description, it is the general idea.

---

