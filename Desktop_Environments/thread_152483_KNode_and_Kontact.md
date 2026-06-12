---
title: "KNode and Kontact"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Mau on 2006-03-30
I've recently discovered Kontact and how it integrates everything into one application.  This prompted me to move from Thunderbird to KMail.

The only problem is getting KNode (for Usenet, I believe) to configure correctly.  I originally installed it with Adept, but it crashed.  So, I reinstalled it with Synaptic and apt-get.

Anyways, the only way I can open KNode is by Alt+F2 or $ knode.  This is odd because it usually installs an item on the KMenu.  When I open KNode though, everything is greyed out, and there are no system preference panels when I configure.  Additionally, Kontact does not recongize it.  Basically it is unusable.

Is there anyway to get KNode working?  I would like to use KNode because it would integrate with Kontact.

**EDIT: It just magically started to work.**

---

### Post by gatekeeper on 2006-03-30
[QUOTE=Mau]I've recently discovered Kontact and how it integrates everything into one application.  This prompted me to move from Thunderbird to KMail.

The only problem is getting KNode (for Usenet, I believe) to configure correctly.  I originally installed it with Adept, but it crashed.  So, I reinstalled it with Synaptic and apt-get.

Anyways, the only way I can open KNode is by Alt+F2 or $ knode.  This is odd because it usually installs an item on the KMenu.  When I open KNode though, everything is greyed out, and there are no system preference panels when I configure.  Additionally, Kontact does not recongize it.  Basically it is unusable.

Is there anyway to get KNode working?  I would like to use KNode because it would integrate with Kontact.

**EDIT: It just magically started to work.**[/QUOTE]

I don't know if this is of any help but when I installed Breezy I found that knode was not on my hard-disk or in my Package Manager. So I found a knode rpm downloaded and installed it using alien (which you would need to install from the package manager). Then started Synaptic up which then recognised it and said there was an upgraded version, so Marked it for upgrade, upgraded it, and it now working fine.

All a little bizarre but that is what worked for me.

---

