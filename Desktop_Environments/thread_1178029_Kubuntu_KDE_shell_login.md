---
title: "Kubuntu KDE shell login"
date: 2009-06-04
forum: Desktop Environments
---

### Post by Mikeee on 2009-06-04
Hi,

Is there away that I can configure kubuntu to present the shell login when I boot the machine up rather than the graphical login. I want to be able to run startx manually.

Thanks

---

### Post by thompson42 on 2009-06-04
This ought to do it.  Not sure about the side effects of this, so it's at your own risk.

sudo mv /etc/rc2.d/S30kdm /etc/rc2.d/noS30kdm

repeat for /etc/rcX.d where X=3, 4, 5

What this does is move the kdm startup script links out of the way.  I haven't checked to see what services depend on kdm, so it's possible that services you're used to won't start after this.  It's easy to reverse this, though:

sudo mv /etc/rc2.d/noS30kdm /etc/rc2.d/S30kdm

and so on.

---

