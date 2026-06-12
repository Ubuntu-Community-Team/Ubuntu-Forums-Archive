---
title: "remove window decoration on one specific window"
date: 2010-05-14
forum: Desktop Environments
---

### Post by Apv507 on 2010-05-14
Is it possible to remove the window decoration from a single window, maybe in compiz or something?

---

### Post by kio_http on 2010-05-15
> **Apv507 said:**
> Is it possible to remove the window decoration from a single window, maybe in compiz or something?

If depends on the application.

---

### Post by mcduck on 2010-05-15
> **Apv507 said:**
> Is it possible to remove the window decoration from a single window, maybe in compiz or something?

Yes, it is.

You can define which windows get decorations and shadows in the Window Decoration-plugin's settings. (In the CompizConfig Settings Manger, of course, so install that if you haven't got it already).

How to actually do that depend a lot on the exact window you are trying to undecorate, but just try to match the window title or name and then enable the invert option.

(For example to undecorate the Gedit window I'd change the entry in the "Decoration Windows"-field from "any" to "!(name=gedit)".)

---

### Post by goldshirt9 on 2010-05-15
thanks for the link :)

---

