---
title: "GNOME and bar"
date: 2012-01-21
forum: Desktop Environments
---

### Post by Jaxke on 2012-01-21
Uhh, done so much googling for this little problem, but it seems my problem is worse than anyone else's...

So, I'm back at Gnome 2(I didn't like Gn3, KDE or Unity...) and I can't find any option to enable the dock or bar which should contain window switcher and task manager. There are currently none, not at the top, nor at the bottom. 

I googled for this problem, but nobody has the same problem as I, at least my problem won't be fixed with the same methods. 

How can I get the bar back? Or how do I delete Gnome 2 and install it again?

Thanks.

(Sorry for being a noob :))

---

### Post by Frogs Hair on 2012-01-21
To add a panel in Gnome 2  right click near the top bottom or side you would like the panel and select new panel . To add items to the panel , right click the panel and select add to panel then choose the items you would like to add from the menu .

To reset panel applets to default run the following command . ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

