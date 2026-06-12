---
title: "Appearance Preferences - not working - HOWTO SOLVE?"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by Lexje on 2007-12-28
Hi folks,

I'm running Gutsy on a Toshiba laptop with nvidia card.
All seems running allright, but I have trouble changing desktop backgrounds.

When I open Appearance Preferences I can't switch to any other tab like Background / Fonts / Interface / Visual Effects.
If I go to Background, the process seems to hang. (It keeps the Theme icons) and when I press +Add a filemanager screen opens, but it hangs....

Also CPU activity increases.

Any suggestions on how to solve this?

Thank you.

Erwin

---

### Post by joshuachad on 2007-12-28
are you using compiz?

---

### Post by Lexje on 2007-12-28
I have to admit that I'm very new to compiz / beryl / AIGL and can't really see the trees through the wood in this matter.
I think I'm running compiz. I have cube effects and such, although I don't really master the settings yet.

---

### Post by Forlong on 2007-12-28
Run this in a terminal and see if there's an error message:
```
gnome-appearance-properties
```

---

### Post by Lexje on 2007-12-28
This is what I get:
erwin@toshiba:/var/log$ gnome-appearance-properties

(gnome-appearance-properties:7962): appearance-properties-WARNING **: Unknown Ta            g: comment


(gnome-appearance-properties:7962): appearance-properties-WARNING **: Unknown Ta            g: comment


(gnome-appearance-properties:7963): Gtk-CRITICAL **: gtk_widget_map: assertion `            GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:7963): Gtk-CRITICAL **: gtk_widget_map: assertion `            GTK_WIDGET_VISIBLE (widget)' failed

---

### Post by Lexje on 2007-12-28
Goog tip!! Thx.
I did a search on the error and found this:
I had gtk-qt-engine installed. I removed it and it worked!

Here is a thread that resolved it for me:
[https://bugs.launchpad.net/bugs/138726](https://bugs.launchpad.net/bugs/138726)

[COLOR="Blue"]sudo apt-get remove gtk-qt-engine[/COLOR]

Worked like a charm for me. Thanks!!

My problem is solved, thank you!!

---

### Post by zdzana on 2008-02-22
I have same problem with this manager and after remove gtk-qt-engine it works fine. But this engine was installed by default and works fine some time. So now i want to get it back. Reinstalling it cause that problem with appearance managet backs again. Any solution how to repair this engine?

---

### Post by FuturePilot on 2008-02-22
I'm not sure, it may be fixed in Hardy. But I didn't think it was installed by default. It wasn't on any of the fresh installs of Gutsy I did.

---

### Post by zdzana on 2008-02-23
My mistake, thanks everybody.

---

