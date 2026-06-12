---
title: "Xabre freezing Xorg"
date: 2006-06-23
forum: Desktop Environments
---

### Post by daigorobr on 2006-06-23
Hello, people...
Recently I tried installing Ubuntu (and then Xubuntu, and then Kubuntu, and then Gentoo) in my second machine.
The fact is that all the times I sudo under X (any administrative tool) it crashes after some time with the infamous "screen frozen, mouse pointer moves" behavior.
Running through the syslog, I find recurrent gconfd failures - complaining about "read-only mandatory path". But not always.
Trying to avoid this bug I went to Xubuntu and then to Kubuntu, but them all use gconfd by default.
Tried, then, using Gentoo. Maybe compiling everything at home would avoid some weird thing. Nothing. It compiles everything great (no segfaults at all) but crashes all the same.
Tried, then, Mandriva 2007 with its Xorg 7.1 (both KDE and Gnome versions) - maybe new versions of everything would go okay. But nothing again.
It only works when I change the X driver from "sis" to "vesa".

My machine is a Celeron 1.7 GHz, with a SiS M947 mobo, 512mb RAM.
The video chipset is Xabre (SiS 330) and I can't find descriptions of failure with it anywhere on the internet.

Before I file a bug both in Malone and Xorg's Bugzilla, does anyone have an opinion?
Sometimes we let the most obvious solutions go and I don't wanna be unfair.

Thank you all.

---

