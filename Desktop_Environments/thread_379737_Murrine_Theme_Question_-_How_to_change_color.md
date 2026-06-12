---
title: "Murrine Theme Question - How to change color"
date: 2007-03-08
forum: Desktop Environments
---

### Post by Foxman2k on 2007-03-08
I am using Murrine Charcoal,  but would like to change a color.

Please see the attached screenshot,  how do I change the white background in the menu?

Thanks!

---

### Post by ComplexNumber on 2007-03-08
> **Foxman2k said:**
> I am using Murrine Charcoal,  but would like to change a color.

Please see the attached screenshot,  how do I change the white background in the menu?

Thanks!
change 'base[NORMAL]' in the gtkrc file from "#ffffff" to whatever you want.

---

### Post by Foxman2k on 2007-03-08
This is the current gtkrc

  base[NORMAL]      = "#393939" # Background, most
  base[PRELIGHT]    = "#272727" # Mouseover menu
  base[ACTIVE]      = "#3c3c3c" # Menu active item in inactive window
  base[SELECTED]    = "#707070" # Menu active item in active window
  base[INSENSITIVE] = "#4c4c4c" # Background, insensitive

---

### Post by ComplexNumber on 2007-03-08
> **Foxman2k said:**
> This is the current gtkrc

  base[NORMAL]      = "#393939" # Background, most
  base[PRELIGHT]    = "#272727" # Mouseover menu
  base[ACTIVE]      = "#3c3c3c" # Menu active item in inactive window
  base[SELECTED]    = "#707070" # Menu active item in active window
  base[INSENSITIVE] = "#4c4c4c" # Background, insensitive
are you sure you've got the right theme? my murrina-charcoal looks like this in the screenshot. you can see further screenshots of murrina-charcoal on gnome-look [here.]("http://gnome-look.org/content/show.php?content=53140") they look like mine.
i've just changed base[NORMAL] to "#ffffff" - see what i get in the 2nd screenshot (i've highlighted the change in red). note the change to the white background.

---

### Post by Foxman2k on 2007-03-08
Figured it out,  for some reason I had a .gtkrc file in my home directory,  which had something like "include etc .etc" which was pointing to another file.

Deleted it and all is good!

Thanks!

---

