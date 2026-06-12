---
title: "[SOLVED] How to disarm CTRL+ALT+BACKSPACE?"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2007-11-04
Hello!

Does somebody know how to disable the CTRL+ALT+BACKSPACE command on X (Xfce) Termninals?


perixx

---

### Post by smartboyathome on 2007-11-04
You wouldn't want to disable it, as that is the reset button for Linux, just like Control+Alt+Delete is the reset button for windows.

---

### Post by perixx on 2007-11-04
I DO want to disable it, otherwise I wouldn't ask ;)
There are still the 'magic keys' left in case of real trouble.


perixx

---

### Post by perixx on 2007-11-07
Does anybody have an idea on how to disable the CTRL+ALT+BACKSPACE keysequence, please? Or at least some suggestion how to remap it to another sequence like CTRL+ALT+SCROLL..?


perixx

---

### Post by perixx on 2008-01-08
*gives it another try*

---

### Post by Forlong on 2008-01-08
Add ```
Option "DontZap"
``` to the **Section "ServerLayout"** of your /etc/X11/xorg.conf

---

### Post by perixx on 2008-01-09
Many thanks, Forlong!!

You don't know how to change the hotkey for that as well, do you? 

perixx

---

### Post by Forlong on 2008-01-09
I don't think that's possible. The sequence is hard-coded into the X-server as a default feature.
You could remap backspace of course, but I guess that's not what you want.

---

### Post by perixx on 2008-01-09
> You could remap backspace of course, but I guess that's not what you want.
No that I don't want ;) But thanks for your info!

perixx

---

