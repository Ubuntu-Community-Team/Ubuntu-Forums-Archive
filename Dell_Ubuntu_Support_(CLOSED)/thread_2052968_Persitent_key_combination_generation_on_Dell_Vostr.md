---
title: "Persitent key combination generation on Dell Vostro 3550"
date: 2012-09-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zuker on 2012-09-04
I have installed Ubuntu 12.04 on my new Dell Vostro 3550 and noticed persistent windows and cursor blinking. When going to console (ctrl+alt+f1) and using 'cat' I see persistent generation of this symbols: '^@'.

Please help!

---

### Post by zuker on 2012-09-04
I get rid of blinking by disabling "Video Bus" id = 8 device under Virtual core keyboard section from
```
xinput list
```

command:
```
sudo xinput set-prop 8 "Device Enabled" 0
```

But after return from console (ctrl+alt+f1 then ctrl+alt+f7) interface is blinking again.

I wonder what this device is? And how I can disable it forever or maybe some drivers needed?

---

### Post by zuker on 2012-09-05
Anybody?
Maybe someone can tell what those "Video Bus" device is?

---

### Post by zuker on 2012-09-05
Bump!

---

### Post by zuker on 2012-09-06
Bump!!

---

### Post by zuker on 2012-09-06
Folks! Need help, please!

---

### Post by zuker on 2012-09-07
Bump!!1

---

### Post by zuker on 2012-09-08
Bump!

---

### Post by zuker on 2012-09-10
**Bump!**

---

### Post by samy234 on 2013-09-03
> **zuker said:**
> I get rid of blinking by disabling "Video Bus" id = 8 device under Virtual core keyboard section from
```
xinput list
```

command:
```
sudo xinput set-prop 8 "Device Enabled" 0
```

But after return from console (ctrl+alt+f1 then ctrl+alt+f7) interface is blinking again.

I wonder what this device is? And how I can disable it forever or maybe some drivers needed?

Thank You!!! you are my personal hero, i have a similar annoying screen flickering problem on the vostro 3550 since 2011! I switched to xfce in the meantime and now came back to gnome and its back. These are my threads about it:
[http://ubuntuforums.org/archive/index.php/t-1897551.html](http://ubuntuforums.org/archive/index.php/t-1897551.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/screen-starts-flickering-problem-with-xorg-and-integrated-intel-graphics-926203/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-starts-flickering-problem-with-xorg-and-integrated-intel-graphics-926203/)

Your workaround seems to work for me, flickering disapears after ```
sudo xinput set-prop 8 "Device Enabled" 0
```
(i did it in a terminal emulator though)

---

### Post by be_max on 2014-01-30
Yes it solves the problem also in my case, I had this problem since 2012!
Did you find some additional information? could be good to investigate on that...

As workaround I put a startup script with the command you suggested.

---

