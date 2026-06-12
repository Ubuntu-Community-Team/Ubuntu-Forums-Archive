---
title: "Font Hinting appears from Nowhere"
date: 2006-02-03
forum: Desktop Environments
---

### Post by Foucault on 2006-02-03
Hi everyone,
I generally hate font hinting, so I have it always turned off from the font preferences dialog. A couple of hours ago I turned off my computer, 'cause I had something to do. Coming back home, I turn on my computer and I surprisingly realize that font hinting is back, although in the font preferences dialog (and in gconf of course) hinting is turned **OFF**. What is going on here?? I have more than a month to touch GNOME's settings as I was fully satisfied with them. I can't remember having done ANYTHING that may inflict gnome font settings.

Please, I need your help!! Everything looks awful in the desktop.

Thank you in advance,
Spyros "Foucault" Stathopoulos

PS: Whatever option I may choose from the hinting section in font preferences the fonts are always the same. Nothing happens. As root everything is working fine, so I guess is a user-specific prob.

---

### Post by dcstar on 2006-02-03
[QUOTE=Foucault]
.......
PS: Whatever option I may choose from the hinting section in font preferences the fonts are always the same. Nothing happens. As root everything is working fine, so I guess is a user-specific prob.[/QUOTE]
Delete the hidden .fonts.conf file in your home directory.

---

### Post by Foucault on 2006-02-04
[QUOTE=dcstar]Delete the hidden .fonts.conf file in your home directory.[/QUOTE]

Thank you dcstar. I've found that file and deleted it. I just cannot understand how did that change.

Anyway thank you for your help ;)

---

