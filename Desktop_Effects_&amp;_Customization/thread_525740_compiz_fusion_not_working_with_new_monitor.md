---
title: "compiz fusion not working with new monitor"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by mpgarate on 2007-08-14
i could easily install compiz fusion before, but when I got my new display things got screwy. I messed up ubuntu in an unrelated way, then reinstalled. following the default method did not work like before. the difference i notice between my old vs new monitors is when I boot from the ubuntu cd, the resolution is 800 by 600, but before it was 1024 by 764 (although both monitors were capable of 1280 x 1024)

---

### Post by EXCiD3 on 2007-08-15
Are you using the proprietary drivers, or the default drivers? Are you using a Nvidia or ATI graphics card?

---

### Post by mpgarate on 2007-08-16
i solved it now, thanks to the irc. ill attach my logs to help anyone who has this problem

(im mr_awesome)



<FusioBot>	To fix your beryl/compiz window decorations (titlebars) with an nVidia graphics card, run « > sudo nvidia-xconfig --add-argb-glx-visuals -d 24 », then restart !X.

---

