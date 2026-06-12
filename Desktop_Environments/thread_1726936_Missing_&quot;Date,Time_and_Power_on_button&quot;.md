---
title: "Missing &quot;Date,Time and Power on button&quot;"
date: 2011-04-11
forum: Desktop Environments
---

### Post by kikiyo on 2011-04-11
May i know why my Date,Time and Power on button missing?

---

### Post by Frogs Hair on 2011-04-11
Hi and Welcome

Right click the top panel  , select add to  panel and from the menu add the Clock and the Indicator Applet Session . Right click the icons and select move to place  them where you want.

---

### Post by kikiyo on 2011-04-11
thanks ya..but how do i get back something like this :(

---

### Post by Frogs Hair on 2011-04-11
> **kikiyo said:**
> thanks ya..but how do i get back something like this :(

Go to Accessories > Terminal on the menu  and copy and paste this command in the terminal and press enter .
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by kikiyo on 2011-04-11
oh my...million thanks!!! xD
ubuntu ROCK \m/:D:D:D:D

---

### Post by Frogs Hair on 2011-04-12
I had to log off before I could check back , glad it worked.

---

### Post by shaquille on 2011-04-13
> **Frogs Hair said:**
> Go to Accessories > Terminal on the menu  and copy and paste this command in the terminal and press enter .
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

I am facing the same problem of missing "Date, Time and Power button". 
I tried you code and that worked. But every time I restart my pc the problem appeared. How to solve the problem permanently?

---

### Post by eromana on 2012-02-10
[Solved] Thanks a million that worked !!


Go to Accessories > Terminal on the menu  and copy and paste this command in the terminal and press enter . 

gconftool --recursive-unset /apps/panel && killall gnome-panel

---

### Post by jasonrisenburg on 2012-02-10
are you using 10.04, and are you going to upgrade when 12.04 comes out?

---

### Post by kikiyo on 2012-02-10
Yea, i'm using 10.4 . i guess 10.4 is the best for local server ;) and yeah! i love linux too! lml

---

