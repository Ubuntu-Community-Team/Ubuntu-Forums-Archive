---
title: "Dramatic improvement in unity 3d performance"
date: 2012-06-14
forum: Desktop Environments
---

### Post by denova on 2012-06-14
I was experiencing extremely poor performance in unity (especially slow rendering while drawing in gimp) and I fixed the problem but I'm not exactly sure how. 

Since unity was performing so poorly I decided to switch to gnome classic. The process went like this:

1. Installed "gnome" package
2. Realized I should have just installed "gnome-panel", uninstall "gnome" and "gdm", reinstall "gnome-panel"
3. Logged into gnome classic session, performance problems solved, gimp is FAST.
4. Logged back into unity shell... performance problems solved there too!

I would very much like to know what package I installed (maybe a dependency that I am not aware of?) that fixed my slow rendering issues. Poor performance in unity seems to be a common issue so a clear fix would be remarkable.

My video hardware from lspci output reads:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

