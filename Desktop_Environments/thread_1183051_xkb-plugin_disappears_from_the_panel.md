---
title: "xkb-plugin disappears from the panel"
date: 2009-06-09
forum: Desktop Environments
---

### Post by GreatEmerald on 2009-06-09
I have an issue with my Xubuntu 9.04: if I add the Keyboard Layouts plugin (xfe4-xkb-plugin) to my XFCE panel, it often randomly disappears, usually on each boot. None of the other plugins do that... Even worse, when the plugin isn't visible on the panel, it seems that I have three layouts installed (I currently have only Lithuanian and English installed) - then I need to switch layouts three times to get the right language, and when it'svisible, I have to that only two times, so it's really confusing.

On a side note, something similar is with the clipboard. It doesn't disappear, but if the Clipboard Manager plugin isn't present in the panel, copy and/or paste actions sometimes fail.

---

### Post by GreatEmerald on 2009-06-16
Any replies yet? :(

---

### Post by robrosenbaum on 2011-01-25
I have the same problem in Xubuntu 10.10. Half way through my session, the xkb plugin disappears from the panel, and my keyboard layout is reset. Looking in 

~/.config/xfce4/panel

The plugin's config file is still there, but it is no longer listed in panels.xml. Any clues?

---

### Post by y6FgBn)~v on 2011-01-25
Found this on the [XKB [Xfce Goodies] page]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin").

Limitations and bugs

Currently the plugin cannot handle well most of the XKB options. Actually it will overwrite all but the first grp: option found in the running configuration. This will change in future versions.

---

