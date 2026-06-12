---
title: "VLC rc3 upgrade throws up dependency error."
date: 2009-06-09
forum: General Help
---

### Post by empty_spaces on 2009-06-09
I'm using the Chris Korn PPA for Vlc. This morning the update manager popped up asking to upgrade from RC2 to RC3.
i went through with the update but hit dependency issues.

See screenshot for the error message.

I tried to uninstall vlc to try and do a fresh vlc install, but it won't allow that either.

Anyone having similar issues? any solutions?

---

### Post by Soul-Sing on 2009-06-09
Take a look at synaptic package manager, are there broken or not installed packages? ( the nox and libvlc2)

---

### Post by empty_spaces on 2009-06-09
There are 3 broken packages - libvlc2, vlc, and vlc-nox

---

### Post by Soul-Sing on 2009-06-09
And isn't possible to reinstall/ or mark them?

or sudo apt-get update

---

### Post by empty_spaces on 2009-06-09
when I mark them for re-install, it says libvlccore2 will also  be installed, I click apply, but then it fails again.

So I marked them all for complete removal which removed all the packages, but also threw up an error for libvlccore2.

When i try to install only the libvlccore2 package from synaptic, it gives an error.

So it looks like the libvlccore2 package has not been configured properly for this upgrade ??
Maybe I upgraded too soon ??

---

### Post by Soul-Sing on 2009-06-09
> So it looks like the libvlccore2 package has not been configured properly for this upgrade ??

possible...

---

### Post by unmole on 2009-06-09
In synaptic see the packages under Not Installed (residual config). If it lists any of the packages you mentioned mark them for complete removal. If that does not work try running:

sudo aptitude purge <name of the package>




P.S. Take a look at computer janitor aswell.......

---

### Post by empty_spaces on 2009-06-09
Ok, looks like I've figured out the issue.

I took a closer look at the error I was getting when trying to install **libvlccore2**. The problem was that **libvlccore0** was still showing up as installed, and it was preventing installation of **libvlccore2**.
If you look at the attached screenshot, **libvlccore0** is related to rc2, which was another clue that it had to be removed.

So I uninstalled **libvlccore0** and then reinstalled **vlc**, and everything installed fine.

Thanks all for your help.

---

