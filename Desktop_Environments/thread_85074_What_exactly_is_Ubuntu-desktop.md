---
title: "What exactly is Ubuntu-desktop?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-11-01
Hello all,

It seems like every other application I want to remove informs me that it'll also remove ubuntu-desktop. I assume it's not such a biggie, since I removed it on the laptop, and it didn't cause any issue, but I would like to know what exactly is that applicaion, and what does it do?

---

### Post by Kyral on 2005-11-01
the *-desktop packages (Ubuntu, Kubuntu, Edubuntu, and Xubuntu) are all so called "Meta-Packages" that exist for the sole reason to install a bunch of other applications. So in Ubuntu-Desktop's case it pulls in Firefox, Evolution, Totem, Rhythmbox, etc

---

### Post by Haegin on 2005-11-01
You can remove it fine without any problems normally. According to the ubuntu team you may need it for upgrading purposes (upgrading to the next release - Dapper Drake) but apart from that, don't worry about it.

---

### Post by ManongTenchi on 2005-11-04
I was wondering this about Ubuntu-desktop: If you choose to uninstall it when removing an application, is it possible to reinstall it, or would that be more trouble than it's worth?

---

### Post by Saul Perdomo on 2005-11-04
[QUOTE=Moonbuzz]Hello all,

It seems like every other application I want to remove informs me that it'll also remove ubuntu-desktop. I assume it's not such a biggie, since I removed it on the laptop, and it didn't cause any issue, but I would like to know what exactly is that applicaion, and what does it do?[/QUOTE]
Well, the best way to know that is finding out which files come within the package.

You can do that using dpkg-query, typing the following in a terminal:

**dpkg-query -L ubuntu-desktop**

Be sure to tell us what you find! Curious minds want to know.


[QUOTE=ManongTenchi]I was wondering this about Ubuntu-desktop: If you choose to uninstall it when removing an application, is it possible to reinstall it, or would that be more trouble than it's worth?[/QUOTE]
I was wondering about it too. In my case, if I want to install it it would also install 66 (!) new packages, which means 260 MB of disk space. I guess the cost/benefit analysis is very personal, but to me it definitely looks like it's not worth the trouble.

-saul

---

