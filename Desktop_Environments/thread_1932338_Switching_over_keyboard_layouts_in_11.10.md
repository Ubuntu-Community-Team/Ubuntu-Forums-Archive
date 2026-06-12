---
title: "Switching over keyboard layouts in 11.10"
date: 2012-02-27
forum: Desktop Environments
---

### Post by zLPrime on 2012-02-27
Hello. I am using three different keyboard layouts: english, russian and greek polythonic. The third one I need only in particular cases, but enough often. I would like use also some of other layouts (for example polish and german) but I worry that it will be too boring to loop all of them.

Is there a way to separate few main layouts from the rest to switch between them in ordinary way (I use Alt+Shift) and make another shortcut for the secondary layouts?

---

### Post by Krytarik on 2012-02-28
> **zLPrime said:**
> Is there a way to separate few main layouts from the rest to switch between them in ordinary way (I use Alt+Shift) and make another shortcut for the secondary layouts?
I don't think so, but it wouldn't really help anyway, since you still can only set up 4 different keyboard layouts. :P Reg. that, I've replied another guy/gal a while back, suggesting creating a custom GUI tool for that:

[http://ubuntuforums.org/showthread.php?p=10333055#post10333055](http://ubuntuforums.org/showthread.php?p=10333055#post10333055)

Notice that, back then, the concerning settings key was still stored in GConf, now it's in DConf; so you'd need to use a command like this instead:
```
gsettings set org.gnome.libgnomekbd.keyboard layouts "['us']"
```If you are inclined to follow that path, don't hesitate to ask me for help, if you need some. :D

Regards.

---

