---
title: "Openbox / Java dont use GTK theme"
date: 2009-05-05
forum: Desktop Environments
---

### Post by ChibiFuriKuri on 2009-05-05
Hi everybody,

I use Openbox with Ubuntu 9.04 and I have a little problem. My Java applications dont use my GTK theme. It uses only this ugly metal-standart-look from Java (I hate this ;-) ). 
I hope someone can help me. (And sorry for my bad english)

---

### Post by eb sol on 2010-08-30
Try :

java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKL ookAndFeel -jar [Your App]

---

