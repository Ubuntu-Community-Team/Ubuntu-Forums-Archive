---
title: "menu-xdg not appearing under Applications"
date: 2006-06-04
forum: Desktop Environments
---

### Post by KilgoreX on 2006-06-04
I installed the Debian menu from the package manager and restarted.  I don't see the menu.

---

### Post by KilgoreX on 2006-06-04
Bump

---

### Post by rölli on 2006-06-11
I had the same problem here on several installations. Also XFCE and fluxbox were not showing the menu. After searching the web for some time and trying some possible solutions, I did at the command line:

sudo dpkg-reconfigure menu-xdg

This did the job. It's possibly a small mistake in the installation of the package.

Cheers, Rölli

---

### Post by iSam24 on 2007-08-27
that didnt work for me i tried lots of things but i just cant get it to work

---

### Post by evolvd on 2008-02-12
yeah doesnt work for me either... any one else have any ideas?

Im running a clean install of Kubuntu 7.1

---

