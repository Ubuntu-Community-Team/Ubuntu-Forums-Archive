---
title: "Refresh panel applet"
date: 2009-10-16
forum: Desktop Environments
---

### Post by denishowe on 2009-10-16
Is there any nicer way for my Perl program to refresh a panel applet's properties than doing "killall gnome-panel"?

I can write new contents to, e.g.
~/.gnome2/panel2.d/default/launchers/wallpaper.pl-1.desktop
but how can I get the applet to refresh itself from the file?

Killing the whole panel is slow, obtrusive and causes pidgin to unminimise.

---

### Post by onyxwolf on 2009-10-16
Good luck with that one I just recently did a similar post, though mine was to refresh a custom application launcher icon. Maybe there is a way to do it with perl but apparently no one knew of a way to do with bash. What are you trying to do with it? My post was [http://ubuntuforums.org/showthread.php?t=1280000 ]("http://ubuntuforums.org/showthread.php?t=1280000").

I ended up having to use zenity notification, but it does the job. Take a look and let me know if it helps. Hopefully your more successful than I was. (The final script is at the bottom of the thread but you can see with how many times I bumped it how no one had that answer. If it wasn't for zhocchao I'd still be jacking around with it, or using killall). :(

---

### Post by denishowe on 2009-10-16
Out of desparation I tried sending every signal in the book to the gnome-panel process (kill -HUP is a fairly common conventional way to ask a process to reload its config) but none of them worked.  They either just terminated the process or were ignored.  Maybe I should UTSL.

---

### Post by fermulator on 2010-07-19
-- annoying --

When a user adds a launcher manually into ~/.gnome2/panel2.d/default/launchers, the panel should automatically notice this and add the launcher...

---

