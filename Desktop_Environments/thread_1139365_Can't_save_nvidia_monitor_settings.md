---
title: "Can't save nvidia monitor settings"
date: 2009-04-27
forum: Desktop Environments
---

### Post by mustanglover32 on 2009-04-27
Setup:

Left screen 19" Acer with DVI-D active
Right screen 17" Dell with VGA active (there is no DVI port on this monitor, otherwise I would have switched them)

Nvidia Graphics Card and yes the drivers are loaded in Ubuntu

Ubuntu always boots to the right monitor and will not let the left monitor be saved as the primary monitor.

Before I upgraded to 9.04 I could at least move the panels over to the left, however now in 9.04 I cannot even move the panels to the other monitor.  Any Ideas??

Thanks,
David

---

### Post by inobe on 2009-04-27
i don't really understand what your trying to do, i do know if your trying to make a setting stick in "nvidia settings" you need super user credentials.

in terminal

```
gksu nvidia-settings
```

be very careful with the settings you make !

---

### Post by mustanglover32 on 2009-04-27
Trying to make the left monitor the primary monitor and dock the panels on the left.

What changes do I need to make in cmd line?

---

### Post by unf on 2009-04-27
[] Merge 

^ do not merge, save clean.

---

