---
title: "Cannot find &quot;Multimedia System Selector&quot;"
date: 2006-07-31
forum: Desktop Environments
---

### Post by jpbennett on 2006-07-31
I cannot find a menu option that I need for troubleshooting sound problems: System->Preferences->Multimedia System Selector. I have no "Multimedia System Selector" option on the Preferences or Administration menus. Somehow I need to make sure the system is set to use ALSA. But also I'm worried there's something wrong if this menu option is missing. Any ideas?

P.S. I'm on Dapper Drake 6.06

---

### Post by bensexson on 2006-07-31
Use Alacarte to enable the multimedia selector.

---

### Post by Ramses de Norre on 2006-07-31
The command is ```
gstreamer-properties

``` and you probably need to have gstreamer installed for it.

---

### Post by jpbennett on 2006-07-31
Excellent. Thanks to both of you. That brought it back.

---

