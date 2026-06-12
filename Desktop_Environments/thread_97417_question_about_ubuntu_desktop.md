---
title: "question about ubuntu desktop"
date: 2005-12-01
forum: Desktop Environments
---

### Post by daedalusman on 2005-12-01
What will I be missing if I uninstall the ubuntu desktop package?

---

### Post by Sutekh on 2005-12-01
Absolutely nothing.  The ubuntu-desktop package is what's referred to as a meta-package.  It installs all the packages that come in the basic Ubuntu desktop installation.  It is not a package itself.

I'll also link you [here]("http://ubuntuforums.org/showthread.php?t=96046&highlight=ubuntu-desktop+remove"); a good HOWTO from aysiu that will remove the packages installed by the ubuntu-desktop meta-package, should you ever want to.

---

### Post by Qrk on 2005-12-01
Nothing. The ubuntu-desktop package is just an easy way to install all of the programs you need. The package itself contains nothing, just a list of dependencies. If you want to actually uninstall the programs that came with ubuntu desktop, like Gnome, you'll have to do that manually.

---

### Post by aysiu on 2005-12-01
[QUOTE=Qrk]If you want to actually uninstall the programs that came with ubuntu desktop, like Gnome, you'll have to do that manually.[/QUOTE] Or use the tutorial I made, which is linked to above.

---

### Post by daedalusman on 2005-12-01
So, if I installed the kubuntu-desktop, I would be able to use either Gnome of KDE?  If so, would that mess anything up, I mean would it be less stable?

---

### Post by aysiu on 2005-12-01
[QUOTE=daedalusman]So, if I installed the kubuntu-desktop, I would be able to use either Gnome of KDE?[/quote] Yes. You could switch back and forth several times a day, if you so wished. > If so, would that mess anything up, I mean would it be less stable? Theoretically? No. In my personal (speaking only for myself--not anyone else on these forums) experience? Possibly.

Also, even if it's stable, your menus can end up awfully cluttered in both Gnome and KDE (especially Gnome, with a whole bunch of KDE applications). 

That's why I wrote that tutorial. Sometimes people think it's a cool idea to install the other desktop environment. Then, after a while, they're thinking, *Yeah, I just want it back the way it was before*. Unfortunately, when they type in ```
sudo apt-get remove kubuntu-desktop
``` nothing uninstalls. Hence, the HowTo.

---

### Post by Sutekh on 2005-12-01
[QUOTE=aysiu]Yes. You could switch back and forth several times a day, if you so wished.  Theoretically? No. In my personal (speaking only for myself--not anyone else on these forums) experience? Possibly.
[/QUOTE]

In my experience it posed a problem using the same user across both GNOME and KDE.  In my current setup I have one user for GNOME and one for KDE, to be extra safe.  But I think for most people there isn't an issue.

---

### Post by aysiu on 2005-12-01
[QUOTE=Sutekh]But I think for most people there isn't an issue.[/QUOTE] Likewise--I think it was only fair, though, to say there's a possibility of instability, seeing as how I experienced it. I know my experience isn't typical, though.

---

