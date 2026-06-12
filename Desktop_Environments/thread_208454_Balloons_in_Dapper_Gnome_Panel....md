---
title: "Balloons in Dapper Gnome Panel..."
date: 2006-07-03
forum: Desktop Environments
---

### Post by Aviatrixie on 2006-07-03
...How do I turn them off? 

   I've looked everywhere and can't figure out how to do it! ( Breezy was easy, but I'm stumped in Dapper. And I've searched the forum, the guides, and my desktop without any luck.)

TIA,

trixie

---

### Post by Zelut on 2006-07-03
I just took a quick look in the gconf-editor & I think I found the option for it (although I haven't tested).

ALT-F2 and start 'gconf-editor'.  The option I found was:
/apps/panel/global/tooltips_enabled
/schemas/apps/panel/global/tooltips_enabled

Take a look at both of those.  Looks like they should turn off the balloon tips you're wanting to get rid of.

---

### Post by Aviatrixie on 2006-07-03
Thanks kuyaedz,

   I unchecked /apps/panel/global/tooltips_enabled and that did the trick! \\:D/ 

trixie



[QUOTE=kuyaedz]I just took a quick look in the gconf-editor & I think I found the option for it (although I haven't tested).

ALT-F2 and start 'gconf-editor'.  The option I found was:
/apps/panel/global/tooltips_enabled
/schemas/apps/panel/global/tooltips_enabled

Take a look at both of those.  Looks like they should turn off the balloon tips you're wanting to get rid of.[/QUOTE]

---

