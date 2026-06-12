---
title: "ubuntuaddon"
date: 2005-10-14
forum: Desktop Environments
---

### Post by majkmil on 2005-10-14
Does the ubuntuaddon cd work with breezy, thanks

---

### Post by professor_chaos on 2005-10-14
Huhh.... Whats a ubutuaddon cd? 

Is that a special membership only cd? Where can I get one? :p 

No, seriously what is it?

---

### Post by majkmil on 2005-10-14
the addon cd is a packadge that installs java, realplayer, xmms, flash, just about anything you can think of effortlessly. I used it in hoary, it is a great tool available here [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/).

---

### Post by codejunkie on 2005-10-14
[quote=professor_chaos]Huhh.... Whats a ubutuaddon cd? 

Is that a special membership only cd? Where can I get one? :p 

No, seriously what is it?[/quote] yes and no some of the packages on the addon cd will still work for example java, w32codecs, libdvdcss2,  but  in order to use them you have to extract the packages and manually install them with ```
sudo dpkg -i packagename.deb
``` because if you use the script it will replace your sources.list file with hoary's and then update and that might cause some apps to break.

---

