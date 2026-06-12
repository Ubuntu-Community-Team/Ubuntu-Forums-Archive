---
title: "Compiz crashed"
date: 2011-02-05
forum: Desktop Environments
---

### Post by usatrooper on 2011-02-05
Whenever I try to get Compiz to work in Ubuntu 10.10 by running compiz --replace at the terminal, it gives me this error:

Launching fallback window manager
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x8fee970)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x8feeab0)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x8feea70)" of type `gboolean'

What does this mean, and how do I get the latest version of emerald themer to load the themes? It was all working fine until I ran the latest Rhythmbox with the visualization plugin, then it all quit working, and started doin weird stuff. I am running this on a Mobile Intel 943GML.

It looked great, too.
:sad:

---

### Post by usatrooper on 2011-02-06
I think I figured out what it is. Compiz crashes when you have 2 monitors hooked up to the Intel 943GML. I read a bug in the Red Hat forums about the same thing. I tried unplugging my monitor, and reloading the WM, and the effects come back. I guess I'll just hafta use one monitor from now on.

:-k

---

### Post by Copper Bezel on 2011-02-06
I've had this problem, too. I don't use a dual-head layout most of the time, but I have DisPlex-Appindicator installed to switch between Metacity and Compiz for when I do.

---

