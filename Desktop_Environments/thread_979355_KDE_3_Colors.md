---
title: "KDE 3 Colors"
date: 2008-11-11
forum: Desktop Environments
---

### Post by snakattak on 2008-11-11
Is there any way to adjust the colors of the kde3 applications in Intrepid? They even include amarok from kde3 as the default, but do not let you modify it at all to look like your kde4 desktop.

---

### Post by lightrush on 2008-11-14
I am interested in this too. Usually qtconfig-qt3 does the job but this time it fails to change the colors. It believes that it did but after all it does not.

This guy [has solved]("http://kubuntuforums.net/forums/index.php?topic=3097927.msg148351#msg148351") it i a dirty way that works (checked). But there should be a bit more elegant solution.

Anyone?

---

### Post by snakattak on 2008-11-15
Your link worked. Agreed that the method is not very clean, but I'll take it. Thanks for sharing.

---

### Post by anjames on 2009-04-08
The simple thing would be a package to install those three files, and a symlink: /usr/bin/kde3colors to a script that calls 'kcmshell colors'? 

More likely though what you want is a script that just copies your kde4 color scheme to your kde3 color scheme.

Hmm...

---

