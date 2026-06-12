---
title: "Change Ctrl+Esc MenuLibre shortcut to something else"
date: 2014-07-06
forum: Desktop Environments
---

### Post by Max the Happy User on 2014-07-06
Hello,

I have Xubuntu 14.04 installed. How can I change the default Ctrl+Esc MenuLibre shortcut? I've searched everywhere (Window Manager, Window Manager Tweaks, in MenuLibre's preferences), but can't find it.
Suggestions on how to do it both via GUI and Terminal are welcome.

If it's impossible to change, how can I at least create an additional shortcut (so both Ctrl+Esc and my shortcut would co-exist)?

Thanks in advance
Max

---

### Post by Max the Happy User on 2014-07-06
I've found one way:

1. vim ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
(substitute "vim" with your editor of choice, for example "mousepad")
2. Find a line containing "xfce4-popup-whiskermenu".
3. In that line substitute "&lt;Primary&gt;Escape" with the shortcut of your choice (e.g. "&lt;Primary&gt;space", as I did).

---

