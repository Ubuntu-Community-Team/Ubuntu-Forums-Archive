---
title: "Is upgrading openoffice to 3 an security issue?"
date: 2009-01-28
forum: General Help
---

### Post by 8200 on 2009-01-28
Hi

My father has to open often micrsoft docs so there is very much improvment for him by upgrading openoffice to 3.0. (he is using Ubuntu 8.10 amd64)


How do you estimate the security issue which happens by adding 
"deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main" to /etc/apt/sources.list and doing the upgrade?


It causes very much packages to upgrade (not only openoffice).


Thank you

Regards
Arthur

---

### Post by kostkon on 2009-01-28
I assume that because you added this PPA and then did a apt-get update, either manually or automatically (if you used the *Software Sources* utility) then Ubuntu checked for any updates. Thus, I assume it's just a coincidence that you also got updates for other packages.

You can check what packages this PPA offers [here]("https://launchpad.net/~openoffice-pkgs/+archive/ppa"). The PPA is safe, of course.

But to be absolutely sure, what other updates did you get?

---

### Post by 8200 on 2009-02-02
Hi kostkon well here you can see what will be upgraded if you add PPA-Openoffice as described:


The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-de openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-l10n-de
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno
The following packages will be upgraded:
  dictionaries-common openoffice.org-emailmerge openoffice.org-l10n-common
  ttf-opensymbol


Regards
Arthur

---

### Post by calc on 2009-03-04
> **8200 said:**
> Hi kostkon well here you can see what will be upgraded if you add PPA-Openoffice as described:


The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-de openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-l10n-de
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-writer python-uno
The following packages will be upgraded:
  dictionaries-common openoffice.org-emailmerge openoffice.org-l10n-common
  ttf-opensymbol


Regards
Arthur

The only package in the above list that isn't produced by the openoffice.org source package is dictionaries-common which is tightly integrated with openoffice.org which was why it had to be updated as well.

---

