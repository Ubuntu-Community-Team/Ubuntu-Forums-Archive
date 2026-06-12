---
title: "beryl problem"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by cloverz7 on 2007-10-01
When I switch my window manager to beryl the title bar doesn't show up...What could cause this problem, I had beryl working on here before I reformatted to have windows for video games..Any help?

---

### Post by aashay on 2007-10-02
try ```
emerald --replace
```

---

### Post by techno-mole on 2007-10-02
if you mean your not getting the window decorations, ie - the close, minimise and maximise buttons you need to edit your xorg.confg file.
so - do the following


First back up /etc/X11/xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back up

(to revert back to original xorg.conf - sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf)

In terminal, run the following command:

sudo gedit /etc/X11/xorg.conf

Then scroll down to the "Screen" section, and insert the following line:

Option "AddARGBGLXVisuals"

Save, close, and restart your X session. Should do the trick.

if that doesnt work try adding - Option "AddARGBGLXVisuals" "true"  to xorg.conf

to re-start your x session press ctrl - alt and backspace together.

cheers

---

### Post by nikkiddl on 2007-10-04
> **techno-mole said:**
> if you mean your not getting the window decorations, ie - the close, minimise and maximise buttons you need to edit your xorg.confg file.
so - do the following


First back up /etc/X11/xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back up

(to revert back to original xorg.conf - sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf)

In terminal, run the following command:

sudo gedit /etc/X11/xorg.conf

Then scroll down to the "Screen" section, and insert the following line:

Option "AddARGBGLXVisuals"

Save, close, and restart your X session. Should do the trick.

if that doesnt work try adding - Option "AddARGBGLXVisuals" "true"  to xorg.conf

to re-start your x session press ctrl - alt and backspace together.

cheers

Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 
Thanks 

In terminal, run the following command:

sudo gedit /etc/X11/xorg.conf

Then scroll down to the "Screen" section, and insert the following line:

Option "AddARGBGLXVisuals"

Save, close, and restart your X session. Should do the trick.

And I done it..............:KS:)

Thank you very very very much:guitar::KS

---

### Post by Motorhead Kaze on 2007-10-04
Thanks from me too.

"Last time" I got Beryl from the Beryl Wiki, and lost title bars.  At that time I had to edit /etc/X11/xorg.conf because there were "Spaces" not "a tab" between the word option and the first quote (picky picky!  Jesus).

This time, there just was no "  Option "AddARGBGLXVisuals" "true"  " so, adding it fixed my compiz right up.  (not Beryl though oddly)

---

