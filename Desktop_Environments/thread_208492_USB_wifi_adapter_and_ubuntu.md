---
title: "USB wifi adapter and ubuntu ?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by ozkan on 2006-07-03
hello i have a USrobotics USB wireless adapter on my desktop system, how i can make my ubuntu be aware of it. how i can use it

---

### Post by Third Thoughts on 2006-07-03
[QUOTE=ozkan]hello i have a USrobotics USB wireless adapter on my desktop system, how i can make my ubuntu be aware of it. how i can use it[/QUOTE]


You're going to want to use the wlan-ng tools. You can install them through synaptic. Just type the command.
```
sudo apt-get install linux-wlan-ng
``` According to synaptic the kernel already has the drivers necessary, but the package will make it work the the infrastructure. Back when I had a USB wireless device this wasn't the case and I had to do some compiling and shell scripting to make things work. If installing the package doesn't work then just post up again and I'll try and help you out.

~Andrew S.

---

