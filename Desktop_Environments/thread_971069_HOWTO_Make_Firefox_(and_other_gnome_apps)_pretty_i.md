---
title: "HOWTO: Make Firefox (and other gnome apps) pretty in Intrepid"
date: 2008-11-04
forum: Desktop Environments
---

### Post by MobiusNZ on 2008-11-04
You might have noticed that when you install firefox in KDE4 it looks like complete ****. Tabs are almost unusable with their colouring, and the form elements are about 50% too large and only look good on websites with light grey backgrounds.

Turns out, the fix is easy - so easy I can't believe its not documented somewhere.

[SIZE="4"]The Fix[/SIZE]

Open up your favourite installer (mine is konsole) and install **human-theme**
```
sudo apt-get install human-theme
```

This is the nice clean Ubuntu theme for gtk (Gnome).

Now, enable it. Go to K -> System Settings -> Appearance. Go down to the **GTK Styles and Fonts** section, and change **GTK Styles** to **Use another style: Human**.

I found this control panel to be a little buggy and I had to change it back and forth before the Apply button lit up, but once I'd done that it was all good.

**Enjoy.** The human theme is only just off colour from the Oxygen style, but its heaps more usable

---

### Post by huntz on 2008-11-08
You have made my day! :)

Finally I can correctly see all web forms, with no style defined.

Thank you again, great tip.

---

