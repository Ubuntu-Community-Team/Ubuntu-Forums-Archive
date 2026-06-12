---
title: "Compiz Burn Effect"
date: 2009-09-28
forum: Desktop Environments
---

### Post by Ravernomina on 2009-09-28
Hello im trying to get Compiz Burn effect to run... but i have no clue what to put for Window Match... Help please Thanks (:

---

### Post by ninjapirate89 on 2009-09-28
Try this:
```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```

That is what it has for the default on mine.

---

### Post by ~sHyLoCk~ on 2009-09-28
> **Ravernomina said:**
> Hello im trying to get Compiz Burn effect to run... but i have no clue what to put for Window Match... Help please Thanks (:

you can turn on animation effect and select Burn from there.

---

### Post by ninjapirate89 on 2009-09-28
If I'm not mistaken, what the OP wants is the info to put in this box. See screenshot.

[ATTACH]130030[/ATTACH]

---

### Post by Mpa4Hu on 2010-02-14
Hello, i have a question. I installed extra options and Compiz configuration managment (or something like this) i configured everithing but i haven't burn effect in menu. how i can add it?

PS: i have karmic koala

---

### Post by Aly007 on 2010-02-14
You have to enable "Animations" and "Animations Add-On" in Effects category. After enable "Animations Add-On" restart CCSM.

---

### Post by jack frost on 2010-11-25
> **Aly007 said:**
> You have to enable "Animations" and "Animations Add-On" in Effects category. After enable "Animations Add-On" restart CCSM.

Thanks.. I always wondered why the burn option did not show up. I just had the magic lamp one on. I didn't really look into it until now.

---

### Post by thebarisaxkid on 2010-11-25
> **Aly007 said:**
> You have to enable "Animations" and "Animations Add-On" in Effects category. After enable "Animations Add-On" restart CCSM.

Make sure you get the following first

```
sudo apt-get install compiz-fuzion-plugins-extra
```

Or is it...

```
sudo apt-get install compiz-fusion-extras-plugin
```

I forget which way it goes.  Try switching them around, and try switching the "s" between plugin and extra. You'll get it eventually

---

### Post by dracoinhell on 2011-01-29
The code is as follows

```
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by smss on 2011-01-29
Hi.
For install Compiz :
   1) run a terminal type :
       1.1)sudo apt-get install compiz-fusion-plugins-extra simple-ccsm
       1.2)Go to Options in the preference, part Paint Burn, and the preferences do.
For use the burn effect :
   later active the paint burn by compiz manager
   Hit (Shift+Super)+LClick (of mouse)

---

### Post by piere simak pampang on 2011-05-11
i can use burn effects on windows but i cant use burn effects on menu, any ideas???

---

