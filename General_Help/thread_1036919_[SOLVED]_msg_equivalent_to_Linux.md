---
title: "[SOLVED] msg equivalent to Linux"
date: 2009-01-11
forum: General Help
---

### Post by HungryMan on 2009-01-11
I have a bash script that works perfectly, except, I don't know if it's done or not. Well, I would know if I executed it from the terminal, but in this case I execute it from thunar... more convenient that way. Is there something like Windows' "msg"?
All I really want it to do is notify me if the script is done with what it needs to do.

---

### Post by lsutiger on 2009-01-11
If you are looking for the equivalent of MessageBox, use xmessage.
for it's usage look at the man page
man xmessage

---

### Post by Taidgh on 2009-01-11
If we're talking about that kind of thing, Zenity seems more widely used. But I guess it's a matter of preference.

---

### Post by Dr Small on 2009-01-11
You can also use zenity for info boxes.

---

### Post by HungryMan on 2009-01-12
Thanks for the info on xmessage and zenity! :D

also I found this in zenity's manpage:
> Display a dialog, asking Microsoft Windows has been found! Would  you like  to remove it?. The return code will be 0 (true in shell) if OK is selected, and 1 (false) if Cancel is selected.
:lolflag:

---

