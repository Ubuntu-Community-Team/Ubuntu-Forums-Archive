---
title: "Ubuntu hangs due to wrong file installed as theme"
date: 2007-03-07
forum: Desktop Environments
---

### Post by zoolake on 2007-03-07
Hi everyone,
  I was fiddling wit h my themes (in system-> preferences-> themes) and I accidentally installed a cursor pack as a theme.  Since I have done this ubuntu hangs during opening and I can only get in using the recovery session of gnome.....does anyone know how to solve this problem or what the config file that may be causing the troubles is called?

---

### Post by ardchoille42 on 2007-03-07
> **zoolake said:**
> Hi everyone,
  I was fiddling wit h my themes (in system-> preferences-> themes) and I accidentally installed a cursor pack as a theme.  Since I have done this ubuntu hangs during opening and I can only get in using the recovery session of gnome.....does anyone know how to solve this problem or what the config file that may be causing the troubles is called?

The themes you install with the theme manager go into ~/.themes. Use the recovery mode to move that theme out of the ~/.themes folder and gnome should load with the default theme, then you can change it.

---

### Post by zoolake on 2007-03-07
Thanks so much ardchoille, it worked perfectly! :)

---

### Post by ComplexNumber on 2007-03-07
> **zoolake said:**
> Hi everyone,
  I was fiddling wit h my themes (in system-> preferences-> themes) and I accidentally installed a cursor pack as a theme.  Since I have done this ubuntu hangs during opening and I can only get in using the recovery session of gnome.....does anyone know how to solve this problem or what the config file that may be causing the troubles is called?
note that cursor themes are installed alongside icons in .icons and /usr/share/icons.


btw here is a tip. find all the cursor files in .icons or /usr/share/icons. go into the directory and look for the index.theme file. add the following line to each of the themes:
Hidden=true


for example, i have added that line to all my icons, and this is what the index.theme file looks like in the Chameleon-Anthracite cusrsor theme:
> 
[Icon Theme]
Name=Chameleon-Anthracite Large 0.5
Comment=Cursor Theme by Giuseppe Benigno <ebengio@gmail.com>
Inherits=whiteglass
**Hidden=true**
Example=left_ptrnow they won't show up alongside your icon themes in the gnome-theme-manager. this is so that they don't end up being selected by mistake.

---

