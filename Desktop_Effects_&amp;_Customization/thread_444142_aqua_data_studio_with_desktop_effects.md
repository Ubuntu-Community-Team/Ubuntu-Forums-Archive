---
title: "aqua data studio with desktop effects"
date: 2007-05-15
forum: Desktop Effects &amp; Customization
---

### Post by mizar001 on 2007-05-15
I'm really disappointed that all works with desktop effects or beryl, except for aqua datastudio where my windows are completely not painted.

To use this app. i have to revert to metacity manager.

Anyone experienced this problem ? or is it an issue with java graphical apps ?

---

### Post by mdwuznik on 2007-05-15
Try disabling ARGB visuals for the problematic apps in beryl-manager.

Michal

---

### Post by mizar001 on 2007-05-15
Thanks, but i disabled ARGB visuals grabbing the window(with beryl manager) and it does not work.

I grabbed the window with the "window title" method and it gave to me "aqua data studio".
So i restarted aqua data studio but still the content of the window is not painted.


I discovered that if i am already in aquadatastudio and i activate beryl the things are working ok. So it's a sort of beryl issue with awt interface.

---

### Post by mdwuznik on 2007-05-17
I know nothing about the app you mention, but remember having to try different solutions for it - Owning program is a fairly "educated guess"

just my .002$
Good luck 
Michal

---

### Post by mocoloco on 2007-06-29
Same issues for me with Aqua Data Studio, and disabling ARGB didn't work for me either.  I had been reverting back to Metacity when using it but didn't know I could start it and then start Beryl afterward so thanks for that tidbit mizar001.  It's a java-based app, so I installed another java app (JAlbum) to test but it doesn't have the same problem, works fine.

---

### Post by zzdrumzz on 2007-08-29
I had the same problem & found this on another site and it worked for me:

To fix this add to your bash profile

export AWT_TOOLKIT=MToolkit

tor just in the respective shell script of the app.

---

### Post by amast on 2008-02-29
From what I have determined, desktop effects does have an affect on Java GUI applications.  Installing NetBeans gave me blank windows.  As soon as I brought the desktop effect down a notch or two, it was fine.

---

### Post by legalizemeth on 2008-04-03
> **zzdrumzz said:**
> I had the same problem & found this on another site and it worked for me:

To fix this add to your bash profile

export AWT_TOOLKIT=MToolkit

tor just in the respective shell script of the app.

Fantastic!  This solved the issue for me.  Thanks!

---

