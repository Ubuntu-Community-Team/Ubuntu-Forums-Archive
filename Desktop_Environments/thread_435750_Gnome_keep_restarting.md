---
title: "Gnome keep restarting"
date: 2007-05-07
forum: Desktop Environments
---

### Post by co0oly on 2007-05-07
Hi there 
i have recently install Unbuntu  fetisty 
then i installed a program that edit splash screen which is called art manager as i think
 and then i have edit the splash screen ....
every thing went will..
until i restart the system to check the new screen  but some thing strange happen the xorg keep restarting after 20 to 30 sec 
when i go to the recovery mode and start gnome there and then open the terminal and type gdm 
the same problem appears again

---

### Post by metalheart on 2007-05-07
Try

```
gdm --config=/etc/gdm/gdm.conf
```

---

