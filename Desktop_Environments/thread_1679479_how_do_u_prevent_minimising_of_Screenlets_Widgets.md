---
title: "how do u prevent minimising of Screenlets Widgets?"
date: 2011-02-01
forum: Desktop Environments
---

### Post by Arminius on 2011-02-01
I'm trying out Screenlets widgets, but whenever I click the "show desktop" button, all the widgets vanish, how do I prevent this happening? so no matter what they will always be under everything else, but there when u minimize all windows.

---

### Post by VCoolio on 2011-02-01
Try this if you use compiz: in System > Prefs > Compiz Config, go to General Preferences and unset "Hide skip taskbar windows".

---

### Post by Arminius on 2011-02-01
I have compiz installed, but it doesn't appear at the location you listed

---

### Post by stinkeye on 2011-02-01
> **Arminius said:**
> I have compiz installed, but it doesn't appear at the location you listed
Alt + F2 and run 
```
ccsm
```


If doesn't work, install with...
```
sudo apt-get install compizconfig-settings-manager
```

You can also set the screenlet to skip task bar by right clicking on 
the screenlet, Properties > Options.

---

### Post by Arminius on 2011-02-02
thank you, that solved the problem, didn't realise that Screenlets was dependent on compiz

---

### Post by VCoolio on 2011-02-03
> **Arminius said:**
> thank you, that solved the problem, didn't realise that Screenlets was dependent on compiz

Well, it's not. You had a window manager problem (compiz is a window manager). Minimizing windows is a wm thing. Screenlets are windows, although they aren't visible on the taskbar. So you had to uncheck the option "Hide skip taskbar windows", which means "don't minimize windows with 'skip taskbar' property". Windows like screenlets or conky are of these kind.

---

### Post by SebSmith on 2011-04-22
works for me also. please mark as solved :)

---

### Post by Claus7 on 2012-02-27
Hello,

> **VCoolio said:**
> Try this if you use compiz: in System > Prefs > Compiz Config, go to General Preferences and unset "Hide skip taskbar windows".

thank you so much! In maverick I went to:
Advanced search->General options and unchecked the option you proposed. I wanted that for cairo clock!

Regards!

---

