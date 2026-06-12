---
title: "nvidia drivers..."
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by MACRI on 2007-05-29
hi, im running beryl and nvidia-glx-new drivers and alls going fine however when i go to change my res in ubuntu i still can't seem to go past 1024x768 but when im in the nvidia setting controller it goes through all the proper res's... i don't remember the terminal command to get back into it lol for the life of me i can't but does anyone know how to make it work with the ubuntu default res changing feature? or make it as default with the nvidia controller?

---

### Post by strumluff on 2007-05-29
You could do this:

First backup your xorg.conf:

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```

Then run nvidia settings with super user privaledges:

```
 sudo nvidia-settings
```

Then change to your preferred resolution and select Save X Configuration (or similar).

That should update the xorg.conf with your default resolution.

---

### Post by MACRI on 2007-05-29
thanks a lot man. worked like a charm :D

---

