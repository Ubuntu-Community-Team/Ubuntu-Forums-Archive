---
title: "Compiz does not start automatically"
date: 2009-02-06
forum: Desktop Environments
---

### Post by pvravi on 2009-02-06
Hi

I have Compiz in my startup programs in System-Preferences-sessions, and I have run compiz --replace many times over. Compiz does not start automatically. 

What's more, running compiz --replace once does not enable all features of compiz. For example, to be able to rotate cube by rolling the mouse - a feature that I use often - I have to run compiz --replace twice after startup. Moreover, any Compiz related programs AWN, Cairo-dock,etc will not start because Compiz does not start. 

So every time I restart I have taken up running compiz --replace twice followed by cairo-dock, and I am getting tired of this. This has been going on for a while now since the Hardy update and through the Intrepid update. 

What's wrong? How do I make this automatic? 

TIA
pvravi

---

### Post by gettinoriginal on 2009-02-06
Check your session startup command for compiz and make sure that it is compiz --replace.  Then the next time you boot up, (if it doesn't start) before typing compiz --replace, go to System, Preferences, Appearance, Visual Effects and make sure it says Extra or Custom.

---

### Post by pvravi on 2009-02-12
> **gettinoriginal said:**
> Check your session startup command for compiz and make sure that it is compiz --replace.  Then the next time you boot up, (if it doesn't start) before typing compiz --replace, go to System, Preferences, Appearance, Visual Effects and make sure it says Extra or Custom.

Thanks, this Works somewhat. However, not everything in Compiz is up by itself. To be able to roll mouse-wheel to flip cube, I need to run Compiz again.

I checked CCSM, there's no real diff before running compiz --replace the second time and after. 

still better than before. At least cairo-dock starts automatically.

---

### Post by gettinoriginal on 2009-02-12
I don't know if you have any special configurations to CCSM, but this will set it all back to default which should let you rotate on scroll:
Compiz Reset to Default  
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by dmstudios on 2011-10-20
> **gettinoriginal said:**
> Check your session startup command for compiz and make sure that it is compiz --replace.  Then the next time you boot up, (if it doesn't start) before typing compiz --replace, go to System, Preferences, Appearance, Visual Effects and make sure it says Extra or Custom.

This is the INCORRECT way of doing this, and is more of a hack. The proper way to do this is to tell Gnome to use compiz as your default window manager and not use metacity at all. 

Simply put this in your ~/.gnomerc (create it if it does not exist yet):

export WINDOW_MANAGER=/usr/bin/compiz

---

