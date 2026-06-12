---
title: "ploblem about install themes"
date: 2009-05-25
forum: Desktop Environments
---

### Post by tonjaa on 2009-05-25
now i use ubuntustudio9.04

i go to download theme GTK2.X name DarkSide and first time i install by drag in to 
Appearance preferences box it's can installed . and then i in stall a themes name BSM suit 
it's can in stall .  and i want to back to use theme DarkSide again i can't find it.
but in   customize theme>  it's has DarkSide Control and window border .
i try to drag theme DrakSide to Appearance preferences again but it's tell.
[COLOR=DarkOrange]install for theme Darkside fail . can't move directory over directory. [/COLOR]
i want to know [COLOR=SeaGreen]true way[/COLOR] to in stall theme . 
and some theme that i can install have some ploblem for theme BSM suit has massage box tell =  this theme will not look as intended because the required icon theme 'nuoveXT.2.2'
is not installed.
how i can do for this ploblem ? 
please tell me the way.

---

### Post by VCoolio on 2009-05-25
First issue workaround is select a theme, use customize to set DarkSide border and controls and then save it like 'MyDarkSide' so it shows up in the appearance window next time.
Second issue is not really an error, it's just a hint. The creator of the theme has an icon theme in mind that goes well with his theme. Install that icon theme if you want, or use another icon theme to your taste with the customize button. If you want to get rid of the 'error' message you can modify the index.theme file in ~/.themes/yourtheme/ with gedit, just modify the line that specifies the icon theme.

---

### Post by tonjaa on 2009-05-25
[COLOR=Green]thank you very much for answer i go to try.[/COLOR]

---

### Post by maxislinux on 2009-05-25
if you mess up too much, delete the .themes directory in your home folder, and start with installiing themes again

---

