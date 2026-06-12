---
title: "Change icon theme but keep icons in the taskbar?"
date: 2010-04-25
forum: Desktop Environments
---

### Post by marginean.m on 2010-04-25
Hi. I really like the new, MacOS-like icons in the taskbar. The problem is that if I change the icon theme (to something else than the themes present in ubuntu by default; I use the Shiki-Wise theme) the nice icons in the taskbar are gone too. Is there a way of keeping those?

---

### Post by Knacker on 2010-04-27
i'm in the same boat. would love a solution to this too. anyone got any ideas?

---

### Post by marginean.m on 2010-05-04
:(

    still hoping

---

### Post by marginean.m on 2010-05-14
:( up...

---

### Post by sakisds on 2010-05-14
Could you point me to the icons you are talking about? (with a screenshot for example)

---

### Post by consindo on 2010-05-14
Hit ALT+F2 then type this in

```
gksu gedit /usr/share/icons/ubuntu-mono-dark/index.theme
```

In the file, locate the line:

```
Inherits=Humanity-Dark,gnome,hicolor
```

Then if you want it to be shiki-wise, change the line to:

```
Inherits=gnome-wise,gnome,hicolor
```

Go to Appearance Prefrences, click customize, click the icons tab and then click Ubuntu Mono Dark.

To change the icon set back, revert it to what the line was before.

It's not pretty, but will do the trick.

---

### Post by marginean.m on 2010-05-14
> **sakisds said:**
> Could you point me to the icons you are talking about? (with a screenshot for example)

Here it is...


LATER EDIT:
consindo's tutorial worked :)

---

### Post by marginean.m on 2010-05-14
> **consindo said:**
> Hit ALT+F2 then type this in

```
gksu gedit /usr/share/icons/ubuntu-mono-dark/index.theme
```

In the file, locate the line:

```
Inherits=Humanity-Dark,gnome,hicolor
```

Then if you want it to be shiki-wise, change the line to:

```
Inherits=shiki-wise,gnome,hicolor
```




   TKS! It worked, with the only correction for those willing to use the Shiki-Wise theme they have to  insert "gnome-wise" not "shiki-wise". 

Have a nice day!

---

