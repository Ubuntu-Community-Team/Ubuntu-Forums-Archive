---
title: "Nvidia Card"
date: 2007-12-21
forum: Gaming &amp; Leisure
---

### Post by TheManzine on 2007-12-21
Hi, I installed wine and I have counter strike 1.6 running fine in open gl and all my settings as on windows but I can't figure out for the life of me how to open my Nvidia settings and turn off v-sync on linux because I am only getting 30fps and on windows that was my problem before. Any help would be appreciated.

---

### Post by cogadh on 2007-12-21
Open a terminal and type "nvidia-settings". However, AFAIK, v-sync is already turned off by default.

---

### Post by TheManzine on 2007-12-21
Hmmm, well now I have a bigger problem unfortunately. I was changing some settings in nvidia-settings and now when I log into ubuntu it says on my monitor "out of range" and will not display. The only other thing I can think that I might have changed was under "screens and graphics" i think and I might have made my monitor "plu g-n-play" but that might have already been turned on and working fine. I have no idea where to start and since I just installed linux about a night ago I wouldn't like to reinstall. Confused..

---

### Post by cogadh on 2007-12-22
The "out of range" message means that you are using a refresh rate setting that is beyond what your monitor is capable of. Pretty much the only way to fix it is to boot Ubuntu into recovery mode, got to /etc/X11 and edit the xorg.conf file to fix whatever is wrong with your refresh rate settings.

---

### Post by Vadi on 2007-12-22
Or simply delete xorg.conf, and the bullerproofx will automatically fix it as best as it can (usually, it was perfect).

---

