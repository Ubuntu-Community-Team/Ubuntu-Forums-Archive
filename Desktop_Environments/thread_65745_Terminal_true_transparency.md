---
title: "Terminal true transparency?"
date: 2005-09-14
forum: Desktop Environments
---

### Post by Strife on 2005-09-14
Pardon my ignorance, but is anyone aware of any way to use, for example, devilspie to call transset on a program when it starts up?

In other words, I want to have a way of "remembering" transparency settings. From browsing the devilspie documentation, it doesn't look like this is possible, but perhaps some other application may be able to do a similar thing?

---

### Post by felipe on 2005-09-26
you could install mrxvt:

[http://materm.sourceforge.net/](http://materm.sourceforge.net/)

it has an internal switch to set a hint for true transparency ;-)

---

### Post by Wolki on 2005-09-28
[QUOTE=Strife]Pardon my ignorance, but is anyone aware of any way to use, for example, devilspie to call transset on a program when it starts up?

In other words, I want to have a way of "remembering" transparency settings. From browsing the devilspie documentation, it doesn't look like this is possible, but perhaps some other application may be able to do a similar thing?[/QUOTE]


From the devilspie documentation:
> DevilsPieActionOpacity

opacity (gdouble): Opacity of window
Range: 0.00 to 1.00
Window is transparent (requires a Composite Manager)

You probably need devilspie 0.10 or newer for this to work, the version in Breezy supports automatic setting of opacity.

---

