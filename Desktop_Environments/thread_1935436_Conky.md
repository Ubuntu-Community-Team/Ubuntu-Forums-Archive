---
title: "Conky"
date: 2012-03-04
forum: Desktop Environments
---

### Post by ric1321 on 2012-03-04
Hi, have you got a sort of a guide to set parameters in the configuration file of conky? Especially what do I have to do if all of my icons on the desktop disappear unless I go over them with the cursor?

---

### Post by Frogs Hair on 2012-03-04
You can copy and paste the .conkyrc here in code tags using the # symbol . changing the own_window_type works in many cases.   

Example:
```
own_window_type normal
``` 
Change to ```
own_window_type conky
```
or```
own_window_type override
```
and```
own_window_type desktop
```

---

