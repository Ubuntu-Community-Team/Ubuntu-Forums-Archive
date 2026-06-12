---
title: "Newbie help - installing software"
date: 2005-10-20
forum: Desktop Environments
---

### Post by hoy_pogi on 2005-10-20
It seems that certain software installed for one user isnt installed for the other users of the computer. a good example of this is the macromedia flash plugin for firefox. How can I install software for all users on the computer&#65311;

&#12393;&#12418;&#12288;&#12354;&#12426;&#12364;&#12392;&#12288;&#12372;&#12374;&#12356;&#12414;&#12377;

---

### Post by codejunkie on 2005-10-20
[quote=hoy_pogi]It seems that certain software installed for one user isnt installed for the other users of the computer. a good example of this is the macromedia flash plugin for firefox. How can I install software for all users on the computer&#65311;

&#12393;&#12418;&#12288;&#12354;&#12426;&#12364;&#12392;&#12288;&#12372;&#12374;&#12356;&#12414;&#12377;[/quote] with the flash plugin if all your users are using the version of firefox that came with ubuntu all you have to do, is enable the extra repositories in your /etc/apt/sources.list file and install this package flashplayer-mozilla this will install flashplayer systemwide. but if they used the firefox version from mozilla.org to install firefox they will have to install the flash plugin manually in the plugins folder where they chose to install firefox into. and the place that i use to manually install software for all users is /usr/nameofapp i haven't had any problems doing it this way but it's really up to you.

---

