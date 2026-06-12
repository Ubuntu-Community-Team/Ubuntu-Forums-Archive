---
title: "slow login problem with edgy and beryl and aiglx (oh my!)"
date: 2007-02-04
forum: Desktop Environments
---

### Post by maayank on 2007-02-04
I've installed beryl with aiglx on ubuntu edgy (specs. below).
All works fine except that the login process is really slow now - the gnome splash screen gets stuck on "window manager" for up to 2 min. - during that time I can open some apps (i.e. terminal) but some I can't (i.e. shutdown window) and it slows down the loading of my startup apps, i.e. network-manager, gdesklets, etc., what makes this really annoying.
Also worth noting is that during these 2 mintues beryl "works" - my windows are all wobbly, the theme is fine and the beryl-manager icon is well placed and works fine in the panel.
Do you guys have any idea on what is causing the problem or what logs might hold the answer?

specs.:
IBM Thinkpad T40
CPU: Intel(R) Pentium(R) M processor 1500MHz
Mem.: 1GB ddr
Gfx: Radeon 7500 with the free xorg drivers

---

### Post by benk on 2007-02-04
Just yesterday I had the same problem. I followed [this tutorial]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft") where it suggests making a new gnome session and making a beryl startup script for that new session. When I did this for whatever reason it would take a long time to load.

I fixed it by ditching the new gnome-session and then I just added beryl-manager as a startup program instead (under System->Preferences->Sessions->Startup Programs tab). Now it works perfectly.

---

### Post by maayank on 2007-02-05
Thank you very much! indeed, it solved the problem :)

---

