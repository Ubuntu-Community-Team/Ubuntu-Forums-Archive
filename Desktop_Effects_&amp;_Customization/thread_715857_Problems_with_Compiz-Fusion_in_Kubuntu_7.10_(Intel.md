---
title: "Problems with Compiz-Fusion in Kubuntu 7.10 (Intel 965GM video card)"
date: 2008-03-05
forum: Desktop Effects &amp; Customization
---

### Post by cangussu.br on 2008-03-05
I have installed the compiz-fusion + emerald packages on my Dell D630 with Intel 965GM video card following a several numbers of tutorials like this [http://ubuntuforums.org/showthread.php?t=601310&highlight=kubuntu](http://ubuntuforums.org/showthread.php?t=601310&highlight=kubuntu) but I couldn't run compiz.
When I ran the command $compiz --replace -c emerald& I received this message:

Checking for Xgl: not present.
Blacklisted PCIID '8086:2a02' found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

I've run the command $glxinfo | grep direct and the rendering is enabled:

$direct rendering: yes

If I tried to use compiz by using the fusion-icon, I can start compiz but I can't run any emerald theme so the windows borders don't appear. When I tried to change the default kde window decorator to emerald the fusion-icon was crashed.

Can anyone help me?

---

### Post by cmavr8 on 2008-03-11
[http://ubuntuforums.org/showthread.php?t=583977&highlight=965gm](http://ubuntuforums.org/showthread.php?t=583977&highlight=965gm)

---

