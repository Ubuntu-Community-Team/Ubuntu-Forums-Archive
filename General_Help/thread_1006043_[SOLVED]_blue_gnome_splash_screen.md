---
title: "[SOLVED] blue gnome splash screen"
date: 2008-12-08
forum: General Help
---

### Post by freshnrg on 2008-12-08
I know it might be really stupid and it probably is but I just don't know how can I get rid of that stupid gnome splash screen???:mad:

---

### Post by eternalnewbee on 2008-12-09
> I know it might be really stupid and it probably is but I just don't know how can I get rid of that stupid gnome splash screen???
Have you tried in **Main Menu > System > Aadministration > Login Window > Local**?

---

### Post by mcduck on 2008-12-09
The same way you used to enable it? It shouldn't even be enabled by default..

Anyway, hit Alt-F2 and run "gconf-editor" to start the Configuration Editor. Then use that to browse to aps/gnome-session/options and disable the "show_splash_screen"-option.

---

### Post by freshnrg on 2008-12-09
I don't know how does that happen cos I was just trying to install some themes and after that I saw this splash screen. anyway cheers mcduck it works, of course ;)

---

### Post by eternalnewbee on 2008-12-09
Please remember, when your problem is solved to mark the thread as solved.
You can do that under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

