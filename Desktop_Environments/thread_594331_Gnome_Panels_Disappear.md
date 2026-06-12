---
title: "Gnome Panels Disappear"
date: 2007-10-27
forum: Desktop Environments
---

### Post by tregetour on 2007-10-27
Recently upgraded to Gibbon. When I switch workplaces my Gnome panels disappear and I can't get them back. Any ideas what's going on and how to fix it?

---

### Post by ChrisShome on 2007-10-27
I had similar problems and found advice on a forum. The problem seems to be related to Compiz.
Go to System/Preferences/Appearances and choose the tab "Visual Effects" 
Select "None" . See what happens. If stable after restarting (or restarting xorg - Ctrl+Alt+backspace) then try turning on visual effects again.

I had lots of problems including losing the top and bottom panels on windows and problems like yours before finding this solution. Stable since then.

Good luck.

---

### Post by dazlari on 2007-10-28
I also have experienced this problem after a system crash. The gnome menu was down and ALT-F2 was out, and restarting the desktop ALT-CTRL-BKSP returned me to the same place! 

I could however create a launcher on the desktop via a right-click, the first of which I attached /usr/bin/nautilus and then I used it to browse the usr/bin folder (highly non-scientific I might add  ;) ). I finally noticed in the gnome-system-monitor (and I have seen this on another thread) that a gnome-panel job was chewing up 1 of the 2 CPUs I have. I killed the task, and re-ran gnome-panel and up popped the menu. It survived the next login so I'm happy for now.

Hope this helps.

---

