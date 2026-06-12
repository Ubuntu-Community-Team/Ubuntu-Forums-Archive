---
title: "Desktop effects"
date: 2010-11-04
forum: Desktop Environments
---

### Post by Choob on 2010-11-04
Hello, I'm completley new to Ubuntu and now I'm trying to use the desktop effects, i used all tut but nothing happens when i type compiz-check this happens :

```
Blacklisted PCI ID 8086:2562 detected

Launching fallback window manager
```I tried to type this into terminal but nothing happens :

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```Please help me!

---

### Post by 3Miro on 2010-11-04
What is your video card and what do you get when you go to System -> Admin -> Hardware Manager.

---

### Post by Choob on 2010-11-04
My graphic card is Intel(r)845G/845GL
And when i go to Hardware Manager nothing appears =/

---

### Post by Choob on 2010-11-04
Buuump

---

### Post by 3Miro on 2010-11-04
Bad news. Your video card is way too old to support OpenGL effects. What you can do is to hit Alt + F2, then type
```
gconf-editor
```
find apps -> metacity -> general and enable "composition". This should work and give you simple transparency for different parts of your desktop.

---

