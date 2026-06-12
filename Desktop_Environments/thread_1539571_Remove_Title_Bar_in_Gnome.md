---
title: "Remove Title Bar in Gnome"
date: 2010-07-26
forum: Desktop Environments
---

### Post by wanzeo on 2010-07-26
Forgive me if this has already been talked about, but I could not find the thread anywhere. What I am trying to do is remove the title bar completely in gnome, it would be nice to be able to choose which applications had the bar and which did not, but I would be perfectly satisfied with just removing them from every window. I assume this is controlled by the window manager which would make it a metacity setting? Anyway, I have an 11in screen on my netbook and I cannot stand having such a big chunk of real estate wasted by such a useless feature, especially when I can perform all the window functions with keyboard shortcuts. Thanks for your thoughts.

---

### Post by hhh on 2010-07-26
Not exactly what you wanted, but check this out...
[http://gnome-look.org/content/show.php/dust+metacity+mod+-+no+title+bar+on+max?content=93631](http://gnome-look.org/content/show.php/dust+metacity+mod+-+no+title+bar+on+max?content=93631)

---

### Post by wojox on 2010-07-26
Open Synaptic and look for maximus. It's used in UNR to save real estate.

---

### Post by nothingspecial on 2010-07-27
> **wanzeo said:**
> What I am trying to do is remove the title bar completely in gnome, it would be nice to be able to choose which applications had the bar and which did not, 

If your machine can run compiz, then install compizconfig-settings-manager.

Then go into the window decoration plugin and in the decoration windows box add each application in brackets, starting with ! spaced with an &

That didn`t explain it very well eg

```
(!name=gnome-terminal) & (!class=totem)
```

That`s mine, so gnome-terminal and totem don`t have the title bar.

---

### Post by mikewhatever on 2010-07-27
I wish there was a simple way to do it. Perhaps you could find a custom theme that gets rid of the title bar. I always reduce its size by shrinking the title bar font under Appearance/Fonts.

---

### Post by nothingspecial on 2010-07-27
If you want to get rid of them all (and you are running compiz)

```
sudo mv /usr/bin/compiz-decorator ~/.decorator.bak
```

If you want them back

```
sudo mv ~/.decorator.bak /usr/bin/compiz-decorator
```

---

