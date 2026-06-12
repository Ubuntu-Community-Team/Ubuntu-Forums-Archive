---
title: "Toolbar disappeared from desktop"
date: 2010-02-10
forum: Desktop Environments
---

### Post by abelito8 on 2010-02-10
Hi, 

I am using xubuntu 9.10 on an AA1 160 GB and 1RAM
the last time I logged out, my toolbar disappeared (I am talking of the bar where you have the menus Application and Places and where I also have a shortcut to the connection manager, battery monitor etc)

this had already happened to me with xubuntu 9.04 (and was the reason why I had moved to Ubuntu) ....I did not do anything to change the settings

is this a bug or there is a way to understand how to put the bar back?

thank you

---

### Post by XubuRoxMySox on 2010-02-10
*Right*-click anywhere on the desktop, choose Applications > Settings > Panel.

You can restore a panel from there, and then right-click on the panel to edit what's in the panel (including a taskbar if that's what you were asking), choose icons, etc. 

-Robin

---

### Post by abelito8 on 2010-02-12
Thank you for this reply ; Actually if I do that nothing happens, this is why I thought it is a bug (also because I did not touch anything and the toolbar just disappeared)

any ways to check what happened through the terminal?

---

### Post by denham2010 on 2010-02-12
Open a terminal and enter:

```
xfce4-panel &
```

That should restart your panel, and then you will be able to access the panel settings as mentioned above.

Xfce is slightly different from Gnome in that it allows you to not have any panels if you wish, whereas in Gnome, you must have at least 1.

Cheers.

---

### Post by abelito8 on 2010-02-13
Thanks so much, it worked

---

