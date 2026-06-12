---
title: "How can one disable mnemonics for a specific app?"
date: 2022-04-03
forum: Desktop Environments
---

### Post by KBar on 2022-04-03
In this specific case, [*xfce4-appmenu-plugin*]("https://launchpad.net/ubuntu/+source/vala-panel-appmenu") is the app. 

Setting **gtk-enable-mnemonics** to 0 in *~/.config/gtk-3.0/settings.ini* disables them for all GTK apps, which is not exactly optimal.

I'd like to disable them just for the global app menu and maybe a couple of more apps. How can I do this?

---

### Post by vanadium on 2022-04-03
This is a gtk feature, so it is all or nothing. The feature actually was deprecated since version 3.10, so if it still works it is a matter of coincidence.

---

