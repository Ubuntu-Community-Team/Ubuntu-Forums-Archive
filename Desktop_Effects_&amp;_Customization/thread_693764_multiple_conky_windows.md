---
title: "multiple conky windows"
date: 2008-02-11
forum: Desktop Effects &amp; Customization
---

### Post by thefatmoop on 2008-02-11
So i have a conky pre-written script that i remade... but it's taking up a good deal of space, is it possible to have another conky area that will be in a different corner of my screen? 

i want to display a part of 
```
 tail -f /var/log/syslog 
```
obviously i'll truncate it in the conky config

---

### Post by notwen on 2008-02-11
create your conky configs

ie. conkyrc1 & conkyrc2

then simply start them using:

```
conky -c conkyrc1
```
```
conky -c conkyrc2
```

---

