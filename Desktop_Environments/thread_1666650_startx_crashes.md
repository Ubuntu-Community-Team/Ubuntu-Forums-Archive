---
title: "startx crashes"
date: 2011-01-14
forum: Desktop Environments
---

### Post by stamoulohta on 2011-01-14
Hi to all,

I'm very new to linux and setting up maverick was time consuming and very hard as a task for me. This is the reason which makes reinstalling to be my last resort, not to mention that I hoped I left all these behind me by dumping Windows...

So, after the last Update, my PC crashes when trying to load Xserver. I can boot in the "recovery mode" from grub and then choose "resume" from the menu. This takes me to tty1. From there if I try to startx my computer crashes again and I'm left with a black screen with no hints as to what went wrong. I even tried ```
startx -verbose > /filename.txt
``` but the file stays empty because apparently my computer hangs before it has the chance to write anything to it.

Finally, I went to the /etc/X11 directory and searched for any xorg.conf backup files. I only found a xorg.conf.fglrx-0 which I renamed to xorg.conf and tried to load xserver again with the exact same result. 

Please guys, help me out a bit here! I thank you in advance,
George.

PS: Ctrl+Alt+Backspace doesn't work either.

---

### Post by stamoulohta on 2011-01-14
Come on guys, You are all I have to hope for!!

---

### Post by stamoulohta on 2011-01-15
OK, solved by reinstalling my ATI drivers who take care the xorg.conf file by themselves. I still have some screen geometry issues but I think I can manage them.

---

