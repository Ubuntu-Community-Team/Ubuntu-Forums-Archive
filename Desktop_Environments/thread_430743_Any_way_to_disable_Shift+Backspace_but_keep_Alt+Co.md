---
title: "Any way to disable Shift+Backspace but keep Alt+Control+Backspace?"
date: 2007-05-02
forum: Desktop Environments
---

### Post by khughitt on 2007-05-02
Hi,

I Disabled the "Shift+Backspace" shortcut from killing X-Windows because i type fast and end up accidentally killing x-windows at least once a day with this feature on. I would like to still be able to have some keyboard shortcut for killing x-windows, ideally "CONTROL + ALT + BACKSPACE", which i believe was also enabled by default.

There are a couple of different ways of stopping shift+backspace, this time i believe i used the 'dont zap' xorg.conf modification.

Does anyone know how i could get rid of one but not the other?

Any help would be much appreciated.
Thanks!

---

### Post by aidanr on 2007-05-02
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

works for me and i still have ctrl+alt+backspace

---

### Post by khughitt on 2007-05-02
Did you only have to run once? Or did you add to .profile or the xmodmap  config file (i forget what it's called)..

---

### Post by aidanr on 2007-05-02
you can add ```
keycode 22 = BackSpace BackSpace Terminate_Server
``` to ~/.Xmodmap

i added ```
#!/bin/bash/
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
``` to /usr/local/bin/shiftbackspace, made it executable and added shiftbackspace to my startup items

but that was ages ago before i knew to add it to ~/.Xmodmap, i should probably change it

---

### Post by khughitt on 2007-05-04
Awesome- worked great.. Thanks!

---

