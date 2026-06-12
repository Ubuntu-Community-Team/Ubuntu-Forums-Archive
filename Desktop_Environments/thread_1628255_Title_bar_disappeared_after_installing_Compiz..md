---
title: "Title bar disappeared after installing Compiz."
date: 2010-11-22
forum: Desktop Environments
---

### Post by bhishan on 2010-11-22
I just installed Compiz in my Ubuntu 10.10 coz I like the cool cube effects. But now I can not see any title bars on any windows.

---

### Post by sikander3786 on 2010-11-22
Press Alt + F2 and reload compiz by

```
compiz --replace
```

If that solves your problem, you can install fusion-icon and add it to startup and then just 2 click and you'll reload the window manager if anything weird happens.

---

### Post by bhishan on 2010-11-22
> **sikander3786 said:**
> Press Alt + F2 and reload compiz by

```
compiz --replace
```



That didn't solve the problem.

---

### Post by Aref.Ariyapour on 2010-11-22
> **bhishan said:**
> That didn't solve the problem.
First of all, I recommend installing fusion-icon. It is so helpful.
Secondly, I think installing Emerald Theme Manager would solve your problem. After installing Emerald, I think you should set Emerald as window decorator in fusion-icon.

---

### Post by bhishan on 2010-11-22
> **Aref.Ariyapour said:**
> First of all, I recommend installing fusion-icon. It is so helpful.
Secondly, I think installing Emerald Theme Manager would solve your problem. After installing Emerald, I think you should set Emerald as window decorator in fusion-icon.

Installing Emerald brought the title bar back working but the title bar is different. It has its own theme and the close, maximize and minimize buttons are on the right hand side. The other option on fusion-icon for window decorator was KDE, isnt there one similar for ubuntu/GNOME. I would prefer the default title bar.

---

### Post by bhishan on 2010-11-22
Lol, it was a easy fix. In the fusion-icon somehow the window manager was set to KDE instead of metacity. I just selected it and everything is working perfect.

---

### Post by bhishan on 2010-12-15
> **bhishan said:**
> Lol, it was a easy fix. In the fusion-icon somehow the window manager was set to KDE instead of metacity. I just selected it and everything is working perfect.

Sorry that did not fix it. I didnt realize that selecting metacity had disabled the cube effect. Compiz had to be selected as the window manager. I saw that in the Window Decorator option there was only KDE4 window decorator and it was being selected. I couldn't find gtk window decorator. So I went to the synaptic package manager and searched for decorator. I marked libdecoration0-dev, libdecoration0, compiz-gnome, compiz, and fusion-icon for installation. Restarted ubuntu. Right clicked on fusion-icon on the top panel, selected GTK window decorator under the window decorator option. And reloaded the window decorator by right clicking the fusion icon on the top panel. And it WORKED!!!! :)

---

### Post by twtgd09 on 2011-04-16
Im having the same issue, tried compiz replace, doesnt work. Dont understand what the OP did with the emerald theme manager, but when i installed, my title bars sporadically would come back. When they dont, sometimes there is an image of the windows it was "over" left in there. help.

---

