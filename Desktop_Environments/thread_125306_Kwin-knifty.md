---
title: "Kwin-knifty"
date: 2006-02-03
forum: Desktop Environments
---

### Post by sphere02 on 2006-02-03
i did add deb from  [http://debian.neo.pl/](http://debian.neo.pl/) to sources.list but knifty dont show up

anyone got knifty window decoration working in breezy and kde 3.5.1

---

### Post by Neo Ex on 2006-02-03
Download the package from the site you wrote: [http://debian.neo.pl/wfmh/pool/main/k/kwin-decor-knifty/kwin-decor-knifty_0.4.2-1_i386.deb](http://debian.neo.pl/wfmh/pool/main/k/kwin-decor-knifty/kwin-decor-knifty_0.4.2-1_i386.deb)

Maybe after installing that package, the Knifty windecoration doesn't show up in KControl: you have to copy or make a link to the Knifty files, which are not in the correct folders. Perform a research to know where they are, and then copy or make a link to them in /usr/share/apps (for the .desktop file) and in /usr/lib/kde3 for the others.

---

