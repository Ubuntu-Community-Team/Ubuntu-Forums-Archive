---
title: "how to change indicator applet clock back to Clock"
date: 2011-10-20
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2011-10-20
I am using the classic desktop on 11.04. I've noticed that the clock no longer has the timezone and weather that I have become used to from before. I think it was the Clock app before, but now it's something else (part of the Indicator Applet?).

Can someone tell me how I can get it back to how it was before?

Thanks,

Max.

---

### Post by crdlb on 2011-10-20
Apparently you can remove the indicator-datetime package to remove that clock. Then you can add the gnome clock applet with right click->add to panel.

---

### Post by Frogs Hair on 2011-10-20
The above will work with Ubuntu Classic session , but with Unity there is no right click add to panel option because it doesn't use the Bonobo panel .

---

### Post by davidmaxwaterman on 2011-10-21
> **Frogs Hair said:**
> The above will work with Ubuntu Classic session , but with Unity there is no right click add to panel option because it doesn't use the Bonobo panel .

In several ways, it seems Unity is a step backwards. I wonder what the benefits are, since there must be some. I wonder if there if there is a way to move the menus back into the windows, rather than at the top of the screen? Is it an attempt to adopt some of the Aqua paradigms - seems quite similar in some ways, IMO?

---

### Post by davidmaxwaterman on 2011-10-21
> **Frogs Hair said:**
> The above will work with Ubuntu Classic session , but with Unity there is no right click add to panel option because it doesn't use the Bonobo panel .

yup, that worked, thanks!

---

### Post by W.McL on 2011-10-21
> **davidmaxwaterman said:**
> I wonder if there if there is a way to move the menus back into the windows, rather than at the top of the screen?

This is possible by uninstalling the appmenu packages.

```

sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt

```

---

### Post by davidmaxwaterman on 2011-10-21
> **W.McL said:**
> This is possible by uninstalling the appmenu packages.

```

sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt

```

Interesting. It strikes me that they have moved the configuration options into apt-get...

Anyway, thanks for the info - perhaps I'll have another go at Unity some day. Perhaps I'll *have* to have a go at it some day (if they remove gnome).

---

