---
title: "No KDE integration in Openoffice 3.2"
date: 2010-03-30
forum: Desktop Environments
---

### Post by Mauror on 2010-03-30
Hi

I can't find any solution for this. After upgrading my Kubuntu (Karmic amd64) and upgrading Openoffice to 3.2, I couldn't install KDE INTEGRATION, because of dependency issues.

_The KPagageKit output is_:
Dependencies of the following packages could not be satisfied: openoffice.org-kde

_Bash gives more information_ about this (translated to English by me):

sudo apt-get install openoffice.org-kde
Following packages have unmet dependencies:
 openoffice.org-kde: Depends: kdebase-runtime (>= 4:4.3.4) but will install 4:4.3.2-0ubuntu4.1
                      Depends: kdelibs5 (>= 4:4.3.4) but will install 4:4.3.2-0ubuntu7.2
E: Broken packages

I hope these data help to solve the problem

Thanks in advance

---

### Post by brucemartin on 2010-03-30
that's because you are trying to install openoffice from the PPA in Karmic and don't have KDE 4.3.4 or higher. upgrade KDE from the kubuntu PPA if you really want to use openoffice 3.2 with kde integration

---

