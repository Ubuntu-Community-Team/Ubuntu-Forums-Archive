---
title: "CompizFusion WindowDecorator - Emerald Themes"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by Adler on 2007-07-03
Hi All,

Like a herd of buffalo we are all switching from Beryl to CompixFusion. I live in the American West, and we say things like that. LOL!

Most of us run all those new cool Desktop effects, but can't seem to merge all those saved Emerald Themes to Fusion. Or, manage themes with Fusion. 

What seems to be missing is a FusionManager, and WindowDecorator. Once changes were made with Beryl we had the opportunity to restart both.

The work done by CompizFusion has been fantastic. But, what am I missing here?

Adler

---

### Post by backflop on 2007-07-03
i had the same problem at first, and what i ended up doing was going into synaptic package manager un installing every thing beryl (just search beryl to find everything). Then I edited my /etc/apt/sources.list to remove all beryl repositiries by typing 
```
sudo gedit /etc/apt/sources.list
```

After that I did (using alt-f2)

```
compiz --replace -c emerald
```

And you should see you emerald theme. If you don't, then re-install emerald. Also if you select a new theme it won't show up until you restart emerald.

I hope that solves you problems.

---

