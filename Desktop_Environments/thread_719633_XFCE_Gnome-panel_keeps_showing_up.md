---
title: "XFCE: Gnome-panel keeps showing up"
date: 2008-03-09
forum: Desktop Environments
---

### Post by kwaanens on 2008-03-09
Hi there

I installed xubuntu-desktop alongside Ubuntu. I fiddled around, and added gnome-panel to my XFCE session. I realised that was a bad idea, but I can't seem to get it to not start with my XFCE session. How do I do this? (What's the file in ~ that I need to remove or change? I tried removing ~/.config/xfce4 and ~/.config/xfce4-session, to no avail)

Thanks!

-- Ketil

---

### Post by soldats on 2008-03-09
It should be in the start-up applications if you added it. Remove it and do alt-f2 and type "xfce4-panel" to get back the xfce panels and restart X and see if that works.

---

### Post by mali2297 on 2008-03-09
Remove the contents of **~/.cache**. 

Also, see if there is anything in **~/.config/autostart**.

---

### Post by kwaanens on 2008-03-09
Thanks!

This last tip worked.

Out of curiousity: Is there any point, with regards to battery life, to run XFCE when I run it with Compiz Fusion? (Compared to Gnome)

---

