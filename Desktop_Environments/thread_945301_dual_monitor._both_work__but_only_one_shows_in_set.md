---
title: "dual monitor. both work  but only one shows in settings"
date: 2008-10-12
forum: Desktop Environments
---

### Post by ThatGuy07 on 2008-10-12
having trouble with dual monitor setup. im on hardy, have an ati hd2400pro on 2 19in monitors. 

under System->Preferences->Screen resolution, it only shows one monitor, but i can set it at 2560x 1024 to get an extended desktop. 

i need to my displays to be swapped, it makes my main as my secondary.  

i have no clue how to do this because every monitor display or resolution app i open only shows one display. if i click detect displays nothing happens. not really sure where to go from here

---

### Post by waspbr on 2008-10-12
you could try sorting out your screens by inputting this command, press alt+F2, then

```
gksu displayconfig-gtk
```

alternatively, if you have an nvidia graphics card you could use nvidia-settings instead (available on synaptic).

Also you could use ccc (catalyst control centre) if you are using an ati card.

both nvidia-settings and ccc have GUIs for monitor config

---

### Post by ThatGuy07 on 2008-10-12
when i run   gksu displayconfig-gtk it only shows screen 1. ive tried ccc but it seems to make hardy reboot every 5 mins or so. this ati card is all ive got, so im at a bit of a loss when it comes to nvidia anything

---

