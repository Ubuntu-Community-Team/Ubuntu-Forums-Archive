---
title: "Color palette for Ambiance Theme"
date: 2010-05-23
forum: Desktop Environments
---

### Post by notesetter on 2010-05-23
Does anyone know where to find the official color palette for the new default theme? I've searched the wiki and can't seem to track it down.

Thanks,

David

---

### Post by marconi75 on 2010-05-25
Hi David,

your desired settings are in the "gtkrc" of the "Ambiance"-theme.
Just have a look under /usr/share/themes/Ambiance/gtk-2.0 

> [FONT=Courier New]# Ambiance theme
#
# Authors:
# Kenneth Wimer <kwwii@ubuntu.com>
# James Schriver <jws141@gmail.com>
#
# Feel free to modify and share!

gtk_color_scheme = "fg_color:#3c3b37\nbg_color:#f0ebe2\nbase_color:#ffffff\ntext_color:#3a3935\nselected_bg_color:#c6b9a6\nselected_fg_color:#323232\ntooltip_bg_color:#000\ntooltip_fg_color:#FFFFFF\nlink_color:#DD4814"

...[/FONT]


Greetz
Marco

---

### Post by notesetter on 2010-05-25
Thanks, Marco.

What I'm after is the recommendations for the purples that have been paired with the theme. I'd like to do some AWN themes to accompany the new scheme.

---

