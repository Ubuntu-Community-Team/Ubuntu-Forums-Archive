---
title: "Kate in XFCE 12.04 upgrade gives symbols as menu font"
date: 2012-04-27
forum: Desktop Environments
---

### Post by coleman_ian on 2012-04-27
I'm wondering if anyone can help me with fixing the fonts in Kate running on XFCE. I updated to 12.04 today and Kate is displaying the menu fonts as symbols (see pic). If anyone can help me with how to restore it, maybe a package was removed during installation, I don't even know where to begin solving this.



I tried going to the second-last menu (the one before help), selecting the last in the list, then the option with the 'spilling paint can' and the second tab which seems to be a font selector, but none of those change the menu fonts. (see pic below)


Thanks in advance for anyone that can help get my menus back.



[IMG]http://i.imgur.com/FNsbp.png[/IMG]

[IMG]http://i.imgur.com/1E6Tx.png[/IMG]

---

### Post by brainwash on 2012-04-27
You can try to adjust the font via *qtconfig*. However, your problem could be caused by the GTK theme engine. Try to select another one.

---

### Post by coleman_ian on 2012-04-27
Thanks for the reply. I installed qtfonts but it was in the same unreadable font so also unusable.

I navigated to the Appearance settings (Settings > Settings Manager > Appearance) and the Fonts tab revealed that the default font was Dingbats. Changing this has resolved the problem.

Strange that it only seemed to affect Kate, the rest of my applications were fine. Anyway, thanks for the inspiration brainwash, I'm surprised I didn't look there in the first place now I think about it... mental blanks can be killer eh...

---

