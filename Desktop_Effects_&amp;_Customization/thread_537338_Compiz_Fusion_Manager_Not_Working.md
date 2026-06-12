---
title: "Compiz Fusion Manager Not Working"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by viergeame on 2007-08-28
I installed Compiz Fusion a little bit ago, and as far as I can tell the install went fine.  I didn't get any errors during it.  The thing is, The config manager won't start.  I've tried opening it from the preferences menu and using alt+f2 to do it that way.  Either way I do it, nothing happens at all.  Is there anything I can do about this?

Also, the guide I used is [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by Vadi on 2007-08-28
Weird. I followed the same article also, it went fine for me. Try reinstalling the **compizconfig-settings-manager** package via synaptic?

---

### Post by viergeame on 2007-08-28
> **Vadi said:**
> Weird. I followed the same article also, it went fine for me. Try reinstalling the **compizconfig-settings-manager** package via synaptic?

I tried that and it made no difference.  So I tried opening it through the terminal and I got this error.

```


nikki@nikki:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

```

---

### Post by michael37 on 2007-08-29
Try [a complete uninstall and reinstall](http://ubuntuforums.org/showthread.php?t=533201).  Worked for me in a similar situation.

Also, use the flat file backend instead of gconf (i.e. start as **compiz --replace** instead of **compiz --replace gconf**).

---

