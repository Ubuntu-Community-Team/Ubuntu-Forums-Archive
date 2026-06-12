---
title: "Firefox form widgets have gray backgrounds"
date: 2008-12-03
forum: General Help
---

### Post by utkjamie on 2008-12-03
The form widgets in Firefox are suddenly showing up with gray backgrounds surrounding them. Text boxes, check boxes, buttons, etc. are all surrounded by a rectangular gray background instead of blending with the background.

Prior to this problem, I was playing around with appearance settings in Kubuntu, including color schemes. There is an option in color settings to "apply colors to non-KDE4 applications." I suspect checking this box may have caused the problem, but don't know for certain -- especially since unchecking the box has not cleared up the Firefox problem.

Anyone have a solution for fixing this problem or anything else I can check that might be causing it?

---

### Post by foolosophy on 2009-02-11
Did you find a solution to this? It's very annoying. Screenshot of gmail:

[[IMG]http://img27.imageshack.us/img27/6572/instantanea1cg0.th.png[/IMG]](http://img27.imageshack.us/my.php?image=instantanea1cg0.png)

They are also too big.

---

### Post by utkjamie on 2009-02-11
> **foolosophy said:**
> Did you find a solution to this? It's very annoying.

Unfortunately, no. I can't believe this is even an issue. KDE should not be messing with the form widgets on web pages. Doing so violates web standards, browser settings, CSS and HTML, and probably a half-dozen other things.

---

### Post by foolosophy on 2009-02-17
Ok, I found it. Install all qtcurve packages (I don't know which one really is the one that makes this work) and then in KDE settings, in Appearance --> GTK styles and fonts   select to use "another" style, and there select Qtcurve. Ta-da!

---

### Post by utkjamie on 2009-02-18
> **foolosophy said:**
> Ok, I found it. Install all qtcurve packages (I don't know which one really is the one that makes this work) and then in KDE settings, in Appearance --> GTK styles and fonts   select to use "another" style, and there select Qtcurve. Ta-da!

QTcurve isn't really a solution. It's just a Band-Aid fix not unlike buying louder speakers for your car so you can't hear the engine rattle. QTcurve pretties up the mess KDE has created but KDE still overrides the widget style settings for individual web sites -- so we don't actually get to see the pages the way the designers intend for us to. Most of the time, it's just an annoyance but I have come across web pages in which this widget "override" breaks the design of a site (e.g. text boxes extend outside of the columns they are supposed to be contained in).

I'm not sure if this is a KDE issue or an issue with Firefox not working with KDE. In either case, it sucks and appears to violate web standards.

---

### Post by foolosophy on 2009-02-18
Yep. I agree. But I think that the problem is neither in Firefox nor KDE, but rather the Kubuntu distribution. I switched to Ubuntu very recently (and I'm planning on leaving it soon) from Gentoo, and I didn't have this issues there. The Kubuntu devs must have packed a modded version of KDE. I'm not sure, though. All distros have their ups and downs.

---

### Post by utkjamie on 2009-02-18
> **foolosophy said:**
> Yep. I agree. But I think that the problem is neither in Firefox nor KDE, but rather the Kubuntu distribution. I switched to Ubuntu very recently (and I'm planning on leaving it soon) from Gentoo, and I didn't have this issues there. The Kubuntu devs must have packed a modded version of KDE. I'm not sure, though. All distros have their ups and downs.

Good to know. I seem to recall reading somewhere that Kubuntu's handling of KDE differs from the norm. This may be another example of that. Thanks for the info!

---

