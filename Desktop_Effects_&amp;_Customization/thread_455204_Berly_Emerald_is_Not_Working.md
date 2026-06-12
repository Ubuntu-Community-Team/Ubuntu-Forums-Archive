---
title: "Berly Emerald is Not Working"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by JordanII on 2007-05-26
I have Beryl and Emerald installed on Ubuntu Feisty Faun and Beryl is working, but not Emerald. When I switch to using Emerald the windows do not have titlebars (windows decorations). How should I fix this? Thanks!

~Jordan

---

### Post by Cresho on 2007-05-26
sudo gedit

/etc/X11/xorg.conf in the “Device” section: add the next couple of lines in Device section

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

you should do a search before posting because i throw this in all the time.

---

### Post by JordanII on 2007-05-26
> **Cresho said:**
> sudo gedit

/etc/X11/xorg.conf in the “Device” section: add the next couple of lines in Device section

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

you should do a search before posting because i throw this in all the time.

Thanks! It worked!

~Jordan

---

