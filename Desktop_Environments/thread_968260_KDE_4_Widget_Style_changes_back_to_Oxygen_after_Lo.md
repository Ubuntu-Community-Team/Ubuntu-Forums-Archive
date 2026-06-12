---
title: "KDE 4 Widget Style changes back to Oxygen after Login"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Yaba on 2008-11-02
I have a strange error after installing Kubuntu Intrepid Ibex, which I didn't experience with KDE 4 on Hardy Heron.

I've installed the QtCurve theme. When I go to the system settings and change the widget style to QtCurve and apply the changes everything is OK. The style is applied and also set in ~/.kde/share/config/kdeglobals.

However when logging out and logging back in, the widget style is reset to Oxygen and the setting is removed from the kdeglobals config file.

Can anyone confirm this behaviour or even know a workaround?

---

### Post by okke on 2008-11-04
I can confirm this using QTCurve also. I think it's sometimes also happening even without logging off. Some apps just somehow change the style. :-?

---

### Post by RingWraith on 2008-11-06
I confirm it too. Very annoying :-|. I thought about uninstalling the Oxygen widget theme, but it seems to be hard wired into KDE4.

---

### Post by RingWraith on 2008-11-06
There is a bug filed in Launchpad about this (bug #281016: QtCurve style is not remembered).

The workaround given there:

> The easiest solution in my point of view is to change/add the following entry

[General]
...
widgetStyle=QtCurve

in the file

~/.kde/share/config/kdeglobals

HTH

---

### Post by RingWraith on 2008-11-06
Or, more simple: just change the style to something different than both Oxygen and QTcurve, apply, then change it again to QTcurve.

---

### Post by okke on 2008-11-08
> **RingWraith said:**
> Or, more simple: just change the style to something different than both Oxygen and QTcurve, apply, then change it again to QTcurve.

This seems to work, strange... but thanks. :D
Should be fixed, tho.

---

### Post by Yaba on 2008-12-01
I can confirm that entering the [FONT="Fixedsys"]widgetStyle=QtCurve[/FONT] in [FONT="Fixedsys"]kdeglobals[/FONT] works. However I can not confirm that switching the style to a different than Oxygen and QtCurve and switching back to QtCurve works.

---

### Post by UrbanSlayer on 2008-12-17
Phew, I thought this was just me.  Was starting to get annoying..heh

Now just to work out why my mouse theme keeps resetting...

---

### Post by Zalbor on 2008-12-20
Switching to another style and back doesn't work.
As for the kdeglobals file, I opened it and that entry is already there, so what am I supposed to change?

---

### Post by Yaba on 2008-12-20
> **Zalbor said:**
> Switching to another style and back doesn't work.
As for the kdeglobals file, I opened it and that entry is already there, so what am I supposed to change?

Capitalization is important.

For me it was

[FONT="Courier New"]widgetStyle=qtcurve[/FONT]

which did not work. After changing it to

[FONT="Courier New"]widgetStyle=QtCurve[/FONT]

it worked.

---

### Post by Zalbor on 2008-12-20
Thanks! That's exactly what I needed! :D

---

