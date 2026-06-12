---
title: "Disabled Blutooth in Vostro 1320"
date: 2010-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ahmad.baei@gmail.com on 2010-11-16
Hi

I removed <bluetooth> , <gnome-bluetooth> and .... packages from my system wrongly. Then, I install them from Synaptic again. But now, Bluetooth of my laptop(Vostro 1320) will activate only when bluetooth key being ON in boot time of Ubuntu. Otherwise, if me turn on bluetooth during the running time of Ubuntu, blutooth will not enable, and one error message will show.

Can anyone help me?

---

### Post by ajgreeny on 2010-11-16
Try ```
sudo apt-get install ubuntu-desktop
``` to see if it finds anything else that you removed but have not yet added back.

---

