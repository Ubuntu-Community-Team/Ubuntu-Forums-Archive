---
title: "Mouse acceleration in 14.04"
date: 2015-10-24
forum: Gaming &amp; Leisure
---

### Post by Sorawit_Kongnurat on 2015-10-24
I have tried a lot of configuration from browsing through the internet but I believe there is still some acceleration. I just fully transferred to Ubuntu so my knowledge might not be up to date. I have wipe my hard drive free of window so there is no way back &#128517;.

---

### Post by ajgreeny on 2015-10-24
So what is the problem?

Tell us exactly what you want and someone may be able to help; at the moment you have told us nothing.

---

### Post by Sorawit_Kongnurat on 2015-10-24
I'm sorry if I what I posted wasn't clear. Basically what I want is as close to windows with no acceleration as possible. 800dpi with no acceleration. My mouse is Razer deathadder if that help.

---

### Post by ajgreeny on 2015-10-24
It would help to know what OS you are running, using which desktop environment.

---

### Post by Sorawit_Kongnurat on 2015-10-24
Oh I'm on Ubuntu 14.04 lts &#128512;

---

### Post by MikeCyber on 2015-10-25
I've used I guess in 14.04 something alike:
xinput --set-prop "My logitech Mouse" "Device Accel Constant Deceleration" 0.3
from:
[http://askubuntu.com/questions/205676/how-to-change-mouse-speed-sensitivity](http://askubuntu.com/questions/205676/how-to-change-mouse-speed-sensitivity)
not necessary in 15.04 anymore.

---

### Post by Sorawit_Kongnurat on 2015-10-25
Is there no acceleration in 15.04 ? Why do you set your mouse "Device Accel Constant Deceleration". Shouldn't it be Device Accel Profile (-1) and Device Accel Velocity Scaling (1) which you set ?

---

### Post by eddiefiggie on 2015-10-28
Here's what I did when I had the same issue in 14.04 LTS:

To get a list of all the input devices I did the following at the command line:

```
xinput list
```

I looked for the "ID #" assigned to my mouse, then did this (where ID# is the # associated to your mouse from the above list):

*remove the "<>"*

```
xinput list-props <ID#>
```

This will show you how your mouse is configured.  I adjusted mine with the following:


*remove the "<>"*
```
xinput set-prop '<MOUSE_NAME_AS_SEEN_IN_LIST>' 'Device Accel Profile' -1
xinput set-prop '<MOUSE_NAME_AS_SEEN_IN_LIST>' 'Device Accel Constant Deceleration' 2
```

You can tinker with the "2" value above by increasing the number or decreasing it based on the feel you prefer.

---

### Post by Sorawit_Kongnurat on 2015-10-29
I guess I will have to settle down with just that :D

Thank you for all your answer

---

