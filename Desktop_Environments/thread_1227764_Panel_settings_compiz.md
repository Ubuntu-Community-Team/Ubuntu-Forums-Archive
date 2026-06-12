---
title: "Panel settings compiz"
date: 2009-07-31
forum: Desktop Environments
---

### Post by Chronon on 2009-07-31
I'm running Compiz on Kubuntu (Jaunty).  Everything is pretty much how I want it with one exception.  Shadows and the semi-transparency in my panel are being overlayed with a kind of abstract striped pattern.  Does anyone know how to get rid of/change this?  I don't see anything obvious in the settings manager.

---

### Post by gettinoriginal on 2009-07-31
Right click the panel, properties, choose the background tab, solid color and adjust the transparency you want.  Make sure that the background pattern is unchecked.

---

### Post by Chronon on 2009-07-31
I'll try when I get home.  Just to clarify, though, it sounds like you're saying to change the KDE panel setting, even though the pattern appears to come from Compiz.  (If I switch the window manager to Kwin the panel becomes smooth and transparent like I want.)

Thanks for your advice.  :)

---

### Post by gettinoriginal on 2009-07-31
I don't believe compiz has any control over the panel, but I am not an expert at this.   :D

---

### Post by Chronon on 2009-07-31
I haven't been home to test yet, but I think you are correct about Compiz not affecting the panel (other than secondary effects like additional virtual desktops appearing in the pager widget, for example).  I believe what I am seeing is a patterned drop shadow that's showing through my transparent panel.  This same pattern is present in all window shadows.

---

### Post by gettinoriginal on 2009-07-31
Ok, open CCSM, Effects, Window Decoration, and either change the "shadow color", or change the size of the shadow to your preference.

---

### Post by Zorael on 2009-08-01
On a small note, I don't think the panel is Compiz-aware enough to toggle its transparency when another window compositor than kwin's is running. So Oxygen's panel will remain black (and not turn its blueish tint), and Air's panel will remain grey.

I don't readily remember CCSM, but can't you add an exception for plasma (and by extension, the panel) in one of the plugins? Window Rules or whatnot?

> **gettinoriginal said:**
> Right click the panel, properties, choose the background tab, solid color and adjust the transparency you want.  Make sure that the background pattern is unchecked.
That sounds KDE3-ish. ;3

---

