---
title: "where the heck is compiz config file?"
date: 2008-08-11
forum: Desktop Environments
---

### Post by logos34 on 2008-08-11
I'm going to try once more enabling desktop-effects, see if I can run it on my integrated nvidia...I was able to in the past only once, briefly, after a fresh install of Feisty, it was sluggish but at least I know it's possible on my specs...I was thinking that maybe if I lower the refresh rate and crank up the frambuffer memory it might work a little better.

Problem: if it locks up, how can I disable it from the command line?  Which file and where?

---

### Post by Afkpuz on 2008-08-11
First of all, install the configuration tool which lets you customize animations and everything to your hearts content.

```
sudo apt-get install compizconfig-settings-manager
```

Then, you can find that in System>Preferences>Advanced Desktop Effects Settings



Now, there are two ways to turn compiz on and off.

GUI
Right click on desktop.  Select Change Desktop Background.  Select the visual effects tab and you're there.  Only problem is that when you use the GUI, you're going to get the default settings.  To customize, just choose any on setting in the gui then use the configuration thing you just installed.


CLI
To turn compiz on via the command line, use this
```
compiz --replace
```

To turn it off, use this
```
metacity --replace
```


Hope that helps

---

### Post by logos34 on 2008-08-11
I already have compiz-settings-manager

> **Afkpuz said:**
> Now, there are two ways to turn compiz on and off.

GUI
Right click on desktop.  Select Change Desktop Background.  Select the visual effects tab and you're there.  Only problem is that when you use the GUI, you're going to get the default settings.  To customize, just choose any on setting in the gui then use the configuration thing you just installed.


CLI
To turn compiz on via the command line, use this
```
compiz --replace
```To turn it off, use this
```
metacity --replace
```
Hope that helps

Yeah I hope it works.  Because if the desktop is all wonky the CLI's my only way of disabling effects

---

