---
title: "out of frequency"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by Hutom on 2008-03-31
Every time I log in to Gutsy screen goes blank for few seconds and the dialog box opens:
> out of frequency
HF 64.3 khz
VF 60.0 hz
operating frequency
HF 30 - 54 khz
VF 50 - 120 hz
power management 15 seconds
Then count down begins. After few seconds Ubuntu starts. Same thing happens when I log out of Gutsy. It does not happen with windows. It never happened with Edgy.

Not that it is giving me a great trouble. But may I just know the explanation?

---

### Post by Hutom on 2008-03-31
anybody?

---

### Post by benerivo on 2008-03-31
You may be able to fix this by editing your /etc/X11/xorg.conf file, which holds instructions for your graphical display amongst other things.

In this file there is a section entitled 'Monitor'. Try adding these two lines...

```
Section "Monitor"

HorizSync 30-54 
VertRefresh 50-120

EndSection
```

You should be able to edit it from a live cd, or from a console after you get the error message (using sudo nano /etc/X11/xorg.conf)

---

### Post by Hutom on 2008-04-24
thanks.

---

