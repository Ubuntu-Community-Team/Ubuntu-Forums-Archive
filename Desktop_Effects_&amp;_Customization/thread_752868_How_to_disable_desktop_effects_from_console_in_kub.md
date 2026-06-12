---
title: "How to disable desktop effects from console in kubuntu 804 beta"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by sotoskawasaki on 2008-04-12
Hi.. I just upgraded my kubuntu 710 to 804. When I tried to enable desktop effects (they were disabled) I choose the second one (simple effects) when I pressed apply suddenly  the screen turned white. I rebooted my laptop but nothing. I only get a white screen and my mouse cursor. I only have access to the operating system through the ttys. So how can I disable the desktop effects from the console. Pls help. Thank you....

---

### Post by Tenzer on 2008-04-23
It can be disabled in the config file: ~/.kde4/share/config/kwinrc, if you are running KDE4. You have to change Enabled to "false" right under the line which says: "[Compositing]".

---

