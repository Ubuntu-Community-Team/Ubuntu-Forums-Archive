---
title: "XKB help: how not to lock AltGr in group 2?"
date: 2008-06-14
forum: Desktop Environments
---

### Post by dapfy on 2008-06-14
Hi,

I've long been the proud owner of a custom German XKB keymap, where not only the default few keys have extra symbols via AltGr, but almost all of them (e.g. AltGr-a = æ or AltGr-, = dead cedilla).  Now I've recently been forced to use a notebook with a us(euro) keyboard.  At the same time I switched from (MS) SuSE to Kubuntu 8.04.  I can keep the German external keyboard.  But when I'm on the move I want a similar comfort, plus I switched the 'y' and 'z' keys, to at least keep word typing comfortable.

My first approach was to define a 2nd setup for the additional keyboard and use setxkbmap -keymap to switch as needed.  But even when reinstalling the original file as had been loaded from xorg.conf, suddenly AltGr becomes an Alt (Emacs Meta) key, and the Windows/Hyper also loses its bindings (in my window manager setup).

So I explored and found out about groups :)  I reworked the file, adding a second group for every key that differs.  It drives me crazy.  For some lousy reason (I somewhere read something about old XKB unaware apps, which I do not care about) turning on group 2 also locks AltGr :(  I found that some of the keys, like ISO_Next_Group, also do something with virtualModifier= AltGr, so I used ISO_First/Last_Group instead which does not -- no result.  So I found that compat/basic does group 2 = AltGr, which I also eliminated -- still not better.

HELP PLEASE: what must I do to get two equipotent (base, shift, base-AltGr, shift-AltGr) FOUR_LEVEL(_ALPHABETIC) groups for one key?

best regards
Dnaiel

---

