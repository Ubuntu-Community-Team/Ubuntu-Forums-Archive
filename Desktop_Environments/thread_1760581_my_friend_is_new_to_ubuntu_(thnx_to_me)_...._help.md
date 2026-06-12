---
title: "my friend is new to ubuntu (thnx to me) .... help"
date: 2011-05-17
forum: Desktop Environments
---

### Post by mIXpRo on 2011-05-17
hi all ,
recently i've managed to install ubuntu on three of my windows users friends (ubuntu only without windows) , but one of them got so excited about compiz fusion and cairo-dock 2.3
, so one after noon he calls me to say : i f*** up the ubuntu
i went to him to find this problem i couldn't solve it :
the cairo-dock have a black square around it , the windows won't move or resize also the windows have no title bar (where the maximize minimize exit buttons) , i tried removing compiz & fusion & extra restoring the default gnome panel , and using metacity by alt+f2 then metacity --replace , but it didn't help .


can someone help , pls ,
he have nvidia 9200m gs , ubuntu 11.04 classic (gnome 2.32)

---

### Post by halovivek on 2011-05-17
Can you please post more about the system configuration ?

---

### Post by Copper Bezel on 2011-05-17
Cairo Dock needs a compositing window manager to avoid having that nasty black box around it, and Metacity isn't one by default. It sounds like your friend messed up something in his Compiz settings such that it was crashing. Running Metacity should have brought back the title bars, but not compositing.

To enable compositing in Metacity, navigate to apps -> metacity -> general in gconf-editor and enable compositing_manager.

The best solution, however, would be to reinstall Compiz and make certain that its settings have been reverted to default (since removing the application won't remove its settings unless you use "purge.") You can reset it with this command:

```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by mIXpRo on 2011-05-17
> **Copper Bezel said:**
> Cairo Dock needs a compositing window manager to avoid having that nasty black box around it, and Metacity isn't one by default. It sounds like your friend messed up something in his Compiz settings such that it was crashing. Running Metacity should have brought back the title bars, but not compositing.

To enable compositing in Metacity, navigate to apps -> metacity -> general in gconf-editor and enable compositing_manager.

The best solution, however, would be to reinstall Compiz and make certain that its settings have been reverted to default (since removing the application won't remove its settings unless you use "purge.") You can reset it with this command:

```
gconftool-2 --recursive-unset /apps/compiz
```

sorry it didn't help , i still have to do metacity --replace every time i log on to show the windows title bar and everything

---

### Post by Krytarik on 2011-05-17
What video driver is running?
How was it installed?

If it's the proprietary "nvidia-current" driver installed through "Additional Drivers", try the "nvidia-173" instead.

Also, the path for Compiz' Gconf settings has been changed in Natty, try this:
```
gconftool-2 --recursive-unset /apps/compiz-1
```
Greetings.

---

### Post by mIXpRo on 2011-05-18
thnx that worked

---

### Post by Krytarik on 2011-05-18
> **mIXpRo said:**
> thnx that worked
What precisely?

---

### Post by mIXpRo on 2011-05-19
nvidia-173 and gconftool-2 --recursive-unset /apps/compiz-1

the title bar came back and the dock has no black square around .

---

### Post by Krytarik on 2011-05-19
> **mIXpRo said:**
> nvidia-173 and gconftool-2 --recursive-unset /apps/compiz-1
Hmm, now we don't know what was the culprit.

---

### Post by mIXpRo on 2011-05-21
an update ,
the nvidia-173 driver caused problems when playing movies , so I got back to (recommended) , and it everything works fine , 
so to sum up the solution to this thread was the 
gconftool-2 --recursive-unset /apps/compiz-1

---

