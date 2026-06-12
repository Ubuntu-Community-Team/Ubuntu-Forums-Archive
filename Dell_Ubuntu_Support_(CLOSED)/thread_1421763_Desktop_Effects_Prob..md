---
title: "Desktop Effects Prob."
date: 2010-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maddg3241 on 2010-03-04
My wallpaper and icons disappear:( when I use normal or enhanced desktop effects can you help me

---

### Post by JohnE1 on 2010-03-07
You can access GNOME's Desktop settings with the configuration editor>


1. Run the Configuration Editor.

Using the GUI:

Open: Applications menu, System Tools and select Configuration Editor

OR

Using a console (Terminal window):

Enter: config-editor


2. To Show Desktop, its setting must be checked.

To see the current setting of 'show_desktop', look under:

/apps/nautilus/preferences


Icons won't appear if 'show_desktop' is not checked.

Not sure if it controls the wallpaper, too. So, I did a search for 'wallpaper' in the config editor and located the following settings:

/schemas/apps/compiz/plugins/wallpaper
/schemas/apps/compiz/plugins/wallpaper/screen0
/schemas/apps/compiz/plugins/wallpaper/screen0/options
/apps/compiz/plugins/wallpaper
/apps/compiz/plugins/wallpaper/screen0
/apps/compiz/plugins/wallpaper/screen0/options

Hope that helps!

---

### Post by maddg3241 on 2010-04-26
now that i switched to 10.04 Lucid Lynx It is all fixed!!!!!!!!!! :):P:popcorn::guitar::lolflag:

---

### Post by JohnE1 on 2010-04-26
> **maddg3241 said:**
> now that i switched to 10.04 Lucid Lynx It is all fixed!!!!!!!!!! :):P:popcorn::guitar::lolflag:

Great! Thanks for letting us know your solution.

JohnE1

---

