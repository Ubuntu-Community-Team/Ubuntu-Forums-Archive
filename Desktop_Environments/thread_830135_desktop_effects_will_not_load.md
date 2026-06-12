---
title: "desktop effects will not load"
date: 2008-06-15
forum: Desktop Environments
---

### Post by Mottq on 2008-06-15
I am having a little trouble getting my desktop effect started. The problems started when I uninstalled KDE and Compiz loaded, but I did not have 3D rendering. I tried installing different Nvidia drivers but each time I got the error, "Desktop effects could not be enabled" I ran compiz check and got this message "More than one graphics chip detected -- sorry, the script can not handle that.Aborting."

I check synaptic to see what was installed and it appears I have tNVIDIA binary XFree86 4.x/X.Org 'new' driver 
and

X.Org X server -- NV display driver 

which one will allow me to enable desktop effects
 
Machine is celeron 2.8 gig northwood processor
Nvidia Fx5200 PCI graphics card.

---

### Post by pytheas22 on 2008-06-15
'nv' is the open-source driver, which won't support desktop effects.

I'm not sure exactly where you are now, but I'd recommend installing envy:
```

sudo apt-get install envyng-gtk
```

and running it with:
```

sudo envyng-gtk
```

From there, it's really easy to automatically get the right driver installed and configured.  Please try that and report back.

---

### Post by Mottq on 2008-06-15
I'm all set! Thank you so much for the help. There is NOTHING better than the Ubuntu community!!

---

