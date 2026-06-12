---
title: "Not able to login thrue kdm"
date: 2005-12-25
forum: General Help
---

### Post by GoldBuggie on 2005-12-25
Something has gone wrong on my computer at the moment. When booting up and getting to kdm I login and there it stop. 

When going to console mode and starting everything with "startx" it works. Basically everything is the same but I see some small differences in the configuration. What is the difference of going thrue kdm or doing startx?? Which configuration files are parsed and not? If someone could help me in the right direction I would be happy. I'm soing some error checking but I haven't figured out where the problem lies really.

---

### Post by GoldBuggie on 2005-12-25
Don't know if this might do any difference but when doing a ps ax ane checking the following

* /bin/sh /usr/bin/startx
* xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc -auth /home/forest/.serverauth.8632

* /usr/bin/X11/X -dpi 100 -nolisten tcp

How is xinit started thrue kdm? Anyone know where the config for that is?

---

### Post by GoldBuggie on 2005-12-26
After some more investigating I think I might have stumbled upon the problem. I can start things with startx provided that .xsession is in ~, otherwise it will halt at the exact same place as when going thrue kdm.

I remember cleaning up:rolleyes: some files in home and maybe I removed some .x<yadda yadda> file. Problem is that I do not know which or what should be in it. I will provide a list of my hidden files. Maybe someone could tell me if they have an important file and what is in it.

.DCOPserver_Cybertron__0
.ICEauthority
.Xauthority
.Xsession
.bash_history
.bash_profile
.bash_profile.lang-modified
.bashrc
.bashrc.lang-modified
.cantusrc
.cshrc
.dmrc
.fonts.cache-1
.fonts.conf
.gksu.lock
.gtk_qt_engine_rc
.gtkrc-2.0
.inputrc
.kderc
.kdrill
.lpoptions
.mailcap
.mcoprc
.mime.types
.private-dic.src.tmp
.recently-used
.serverauth.6608
.serverauth.7613
.serverauth.7725
.serverauth.9278
.sversionrc
.toprc
.viminfo
.xcompmgrrc
.xsession

---

