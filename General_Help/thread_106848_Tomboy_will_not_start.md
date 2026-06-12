---
title: "Tomboy will not start"
date: 2005-12-21
forum: General Help
---

### Post by ade234uk on 2005-12-21
I am really interested in getting Tomboy running to take notes. However when I try and run it nothing nothing happens. I have installed / uninstalled twice now using add applications but still the same problem.

Any ideas how to get this going?

---

### Post by 23meg on 2005-12-21
Tried adding into your Gnome panel?

---

### Post by ade234uk on 2005-12-21
It is added to the Gnome panel and will not start. I then set it run in terminal to grab some information and this is what is comes up with.

Tomboy remote control active.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:14247): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

(Tomboy:14247): libtomboy-WARNING **: Binding '<Alt>F11' failed!

---

### Post by 23meg on 2005-12-22
Which version is it? Run gconf-editor and try modifying these values: 

/apps/tomboy/global_keybindings/open_start_here 
/apps/tomboy/global_keybindings/show_note_menu

---

### Post by ade234uk on 2005-12-22
I modified the keys and Tomboy now works. Thank you very much.

---

### Post by 23meg on 2005-12-22
Glad to have helped; BTW, 0.3.3 must be in the backports or will be very soon.

---

