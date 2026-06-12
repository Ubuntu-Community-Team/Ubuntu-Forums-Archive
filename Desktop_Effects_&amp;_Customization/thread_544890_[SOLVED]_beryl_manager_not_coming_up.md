---
title: "[SOLVED] beryl manager not coming up"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by auzy07 on 2007-09-06
i a fairly new user on ubuntu, had it before, went back to windows, got pissed, came back to linux. now i've got everything on how i want it and i went to put beryl and emerald on, i got it going and everything but i cant open the beryl manager to changes all my settings. whenever i type in beryl-manager or beryl into terminal my screen flashes a few times and the bar on top of the windows goes away and they any open programs dont show up on the bottom bar. any suggestions?

---

### Post by o3rat on 2007-09-06
What kernel are you using? Im using 2.6.22.9-generic and beryl-manager runs fine. I know I had a problem with that in 2.6.20.10-generic

---

### Post by auzy07 on 2007-09-06
sorry this is only my second time using linux, were can i find out what kernel im running? i just downloaded it off the site the other day so im pretty sure its the newest one, but i dont know what number it is.

---

### Post by auzy07 on 2007-09-06
o, if it helps any, when i click on the red diamond in the top of the screen it doesnt do anything but i can right click on it and it comes up with a few emerald options

---

### Post by smartboyathome on 2007-09-06
try running beryl manager in a terminal by typing beryl-manager and post the results.

---

### Post by o3rat on 2007-09-06
> **auzy07 said:**
> sorry this is only my second time using linux, were can i find out what kernel im running? i just downloaded it off the site the other day so im pretty sure its the newest one, but i dont know what number it is.

check kernel version```
uname -r
```

---

### Post by auzy07 on 2007-09-06
2.6.20-16-generic

and when i type in beryl-manager a drop down screen comes off my cursor with the options of 
emerald theme manager
reload window manager
select window manager -->

and basicly what happens when i right click on the beryl icon on the top right

---

### Post by smartboyathome on 2007-09-06
It works then. Check to make sure the Beryl settings manager is installed in Synaptic.

---

### Post by auzy07 on 2007-09-06
ya, beryl-manager is there

---

### Post by auzy07 on 2007-09-06
dont worry guys, the settings manager wasnt installed, but i got it and installed it. thanks guys.

---

### Post by ekricyote on 2007-09-29
Is there a way to reload the Beryl window manager (or whatever is the active manager) using a keystroke?

After my screensaver kicks in, time passes and then my monitor display goes blank; when I try to unlock my session, I cannot see anything and I'm forced to restart via Ctrl-Alt-Backspace (restarting GNOME).

---

