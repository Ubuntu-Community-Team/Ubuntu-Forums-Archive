---
title: "ATI 8.42 drivers break Compiz/XGL?"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by shadowplane676 on 2007-12-17
well, i tried to update my ATI drivers from 8.36 to the 8.42 ones and it killed my XGL/Compiz setup, corrupted the video. I spent a while screwing with it to re-install/setup the 8.36 drivers, copied in the backup xorg.conf and alls well again. My question is, what or why does the 8.42 drivers have that breaks this?

HP pavililon ZV6000
AMD 64 2.4
ATI 200M graphics
Kubuntu Feisty x86_64 kernel

---

### Post by Espreon on 2007-12-17
For things like that, you 1st need to uninstall the one from the repos. The rest IDK. There is a tutorial somewhere. If your updating just for the ability to use AIGLX with your ATI card, its not worth it. 8.42 works with AIGLX, but not as well as it does with XGL. Even the ATI developers stated that. Basically if you tried to use AIGLX with 8.42 it would be hella slow. The ATI people are workin on it though.

Its not the update that broke CF/XGL... thats all I know.

---

### Post by shadowplane676 on 2007-12-17
hmmmm, ok. all i know is that the 200M is a PITA to get this stuff working. For whatever reason ive had to always use the manual install of the ATI drivers, as an apt-get or Synaptic install doesn't find anything. Adept has done an OK job keeping up though so *shrug*

---

