---
title: "Is this a bug for default theme? any one could help to fix this problem? pls!"
date: 2009-04-02
forum: General Help
---

### Post by Kelen.Chang on 2009-04-02
I found Below warning messages always showed me while i open program's window with terminal.
so Is this a bug for Human-Murrine theme? or something wrong with me somewhere? any way can fix it?
```
$ gqview Work/temp/2009-04-02-013710_424x498_scrot.png 
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:82: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:111: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:140: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:176: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:210: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
```

---

### Post by TyrantWave on 2009-04-02
Have you tried updating the theme?

---

### Post by Kelen.Chang on 2009-04-03
How do i know what's the version for me right now? i even don't know how to upgrad the theme. :(

---

### Post by kpkeerthi on 2009-04-03
It appears that the GTK theme is still using some of the murrine features that have been deprecated. Update the theme or contact the theme author or switch to a better theme.

---

### Post by Kelen.Chang on 2009-04-03
i did replace words "hilight_ratio" to "highlight_ratio" under file gtkrc. it's worked again.. 
right now, have no warning messages anymore.

---

