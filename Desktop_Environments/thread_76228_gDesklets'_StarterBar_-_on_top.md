---
title: "gDesklets' StarterBar - on top???"
date: 2005-10-14
forum: Desktop Environments
---

### Post by chaumurky on 2005-10-14
I have installed the 'Mac OSX' style StarterBar widget. How do I keep it on top so that I can actually be useful...? :rolleyes:

---

### Post by andremarcel on 2005-10-15
Doesn.t it work with the shortcut for gdesklets shift+F12?

---

### Post by specvwillis on 2005-10-15
Right click on the desklet, click on view source.  Find the line that says 

```
window-flags="below, sticky"
```

and change it to

```
window-flags="above, sticky"
```

then restart the desklet.

---

### Post by xyzzyman on 2005-10-15
The problem with that, is it leaves a large spot around it showing your desktop when a window wants to be behind it.

---

### Post by chaumurky on 2005-10-15
So it does, that's a shame. I may have to look at the other alternatives.

---

### Post by specvwillis on 2005-10-23
> The problem with that, is it leaves a large spot around it showing your desktop when a window wants to be behind it.

The only way to get around that is to enable the translucent feature of Gdesklets.  But, you'll need to get xcompmgr and it may slow down your system.

---

### Post by saldie on 2005-12-10
Has anyone resolved this problem.
The starter bar is gereat, but not very usefull if it's not on top.
Thanks.

---

### Post by zi99y on 2006-01-02
Seems a shame that all that effort was put into this desklet but it cannot be used effectively :(

---

