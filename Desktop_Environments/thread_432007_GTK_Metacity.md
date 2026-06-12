---
title: "GTK Metacity"
date: 2007-05-03
forum: Desktop Environments
---

### Post by Bengaul on 2007-05-03
OK, OK! I give up!

Could someone tell me what GTK & Metacity actually are? What they do? Why GTK & Metacity themes never work. As far as I can tell they are window managers, and they can be themed, but there seems to be extra software needed to get themes to work. Wha am I missing... :confused: Any help to clear this up in my own mind would be fantastic!

Bengaul.

---

### Post by NeoChaosX on 2007-05-03
GTK is the graphical toolkit that forms the basis for Gnome. It tells programs how to draw most of widgets you see on screens like fields, tabs, scrollbars and buttons. It does NOT, however, draw the window borders. That's the job of Metacity.

Metacity is the window manager. It handles where windows are placed and messed with, as well as drawing the borders around windows as mentioned before. These are two completely different components.

If you're running GNOME, you can change the theme for these components in Settings -> Theme. You want to install GTK themes in the list of themes, and Metacity themes in the list of window borders.

---

### Post by Bengaul on 2007-05-03
Thanks for the reply, that seems to answer things a bit. Why is it that GTK seems to be unable to support some themes natively?

---

### Post by mcduck on 2007-05-03
> **Bengaul said:**
> Thanks for the reply, that seems to answer things a bit. Why is it that GTK seems to be unable to support some themes natively?

Themes may be using GTK engines which you don't have installed. Most likely that would be Murrine, Pixbuf or Rezlooks engine that's missing. (All themes using images as parts of the theme need gtk2-engines-pixbuf that is not installed by default.) Murrine is also in Feisty's repositories, so try install at least those 2 and your themes will most likely work.

---

### Post by Bengaul on 2007-05-03
Thank you for the advice. I have struggled to get straight forward info about this issue for a while. I have more to go on now. 

Thanks.:)

---

