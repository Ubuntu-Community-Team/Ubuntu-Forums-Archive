---
title: "Lost gnome session after evolution uninstall / deinstall"
date: 2010-02-04
forum: Desktop Environments
---

### Post by horstkotte on 2010-02-04
I just wanted to write this down in case somebody else ends up like me this morning. 
I had uninstalled evolution recently and not rebooted immediately afterwards. When I rebooted this morning suddenly the gnome session had disappeared from one of the login screen options and I was stuck with IceWM. 
I found all configuration files still present but gnome would just not be an option as login session.
After fiddling around a little I decided to reinstall package ubuntu-desktop which contained evolution (that's when I remembered I had uninstalled evolution). This fixed the problem and all my original desktop settings (including metacity/compiz) were back to normal :D

I am not sure about the dependency of gnome and evolution but I won't touch it again!

---

### Post by sismo on 2010-03-06
horstkotte:

Thanks for this post, I just got same problem on ubuntu-remix on my wife's netbook, we almost ran out of space and thought can reclaim some from software she is not using (including evolution). 

I followed your note and re-install ubuntu-desktop fixed my problem.

Thanks again
Regards.

---

### Post by dannyx on 2011-05-19
Thank [horstkotte]("http://ubuntuforums.org/member.php?u=474780"), it works. I also figured out that if you don't want to bring back evolution (or other unnecessary software that will come together with ubuntu-desktop) you can just reinstall gnome-panel only.

---

