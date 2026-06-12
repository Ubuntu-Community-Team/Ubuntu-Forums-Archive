---
title: "Openbox startup problems"
date: 2009-10-23
forum: Desktop Environments
---

### Post by Haiyadragon on 2009-10-23
I'm trying to run several alias commands and an setxkbmap on Openbox start. I've tried to put the commands in /etc/profile and also in .config/openbox/autostart.sh and in neither case will Openbox pick them op. If I source the files manually after startup the commands work fine.

Any idea where I can put my commands to run them at startup?

---

### Post by compiledkernel on 2009-10-23
[http://gwos.org/udsf/doku.php/software:openbox](http://gwos.org/udsf/doku.php/software:openbox)

Bout half way down the page. 

I normally use the sleeper syntax in my conf 

It does belong in ~/.config/openbox/autostart.sh though.

---

### Post by Haiyadragon on 2009-10-24
Thank you! That did it. Very useful site.

---

