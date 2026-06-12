---
title: "Code for Desktop is eating my cpu"
date: 2015-12-25
forum: Desktop Environments
---

### Post by chkneater on 2015-12-25
Does anyone know what this line is and how to stop it from running?  It is eating up all my cpu for some raisin it will spike up to 35%.  I need  help with this, it is serious and should be triaged as this could severely damage the cpu IF it hasn't already.  I know it has something to do with the screensaver and the desktop, already disabled the screensaver...

" /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none "

---

### Post by grahammechanical on 2015-12-25
On my system lightdm is not running. It is my understanding that once we log in everything switches from the Light Display Manager to the Compiz window compositor/manager & the Unity user interface.

I use the top command to monitor what processes are using up CPU & memory resources.

```
top
```

And lightdm is not running. In your other thread you say that you have switched to GDM instead of LightDM. To do that we stop lightdm & then start gdm. Have you switched back to lightdm again?

Regards.

---

### Post by mc4man on 2015-12-25
> **chkneater said:**
> Does anyone know what this line is and how to stop it from running?  It is eating up all my cpu for some raisin it will spike up to 35%.  I need  help with this, it is serious and should be triaged as this could severely damage the cpu IF it hasn't already.  I know it has something to do with the screensaver and the desktop, already disabled the screensaver...

" /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none "
Elsewhere you say 3-25%, here 35%, neither is "thru the roof" & can't see how 3-35% usage/spikes of a cpu would damage it. 
(3-35% of what cpu?
Anyway the process is not lightdm, it's xorg.

---

### Post by chkneater on 2015-12-25
when it uses a third of your CPU and zero RAM and when BEFORE a header update it was fine, somethiung is wrong mc4mann...and believe it or not a cpu overheating is NOT and ideal situation last I checked; and also I payed more attentnion to THAT command and saw it spiking HIGHER than I thot, sorry bout that but I don't see how quarelling over something so minor is of any help... what makes you think it's X.org and not lightdm since this same topic was an issue in separate threads involving that line but NONE of them menion X as the problem?  What is your input other than JUST that?  Because of the " usrbin/" line? because that is not a command, its a directory??

And Grammechanical; no I did not switch to GDM, I just INSTALLED it which RESTORED the orignal config files for LightDM... when you install GDM, it will ask you if you wanna use gdm or lightgdm...I just chose Lightdm and nothing changed, just the cpu usage.... but Iwas wondering what would happen if I chose GDM instead?

---

### Post by CantankRus on 2015-12-26
Fyi ... 14.04

---

