---
title: "Cannot find Printing after reinstallation of CUPS"
date: 2011-10-11
forum: Desktop Environments
---

### Post by blitzit on 2011-10-11
I recently had a problem with printing on my printer HP 2055dn LaserJet which I am using on a network in my College Lab.

Because of the error I couldn't print any pages, neither could I open *System -> Administration -> Printing*. I thought reinstalling cups would do it and hence as a first step uninstalled the CUPS installation.

I reinstalled CUPS later, all the packages that I thought would be related, but now I don't get Printing in System -> Administration.

:(

I need help installing that package.

---

### Post by blitzit on 2011-10-12
Okay, one problem solved. I realized I needed to reinstall system-config-printer-common and system-config-printer-gnome.

I suppose I know what the problem is. I had played around with the version of Python installed in my system (I had installed Python 2.5.6 because it was needed to make BackInTime work) and now I realize it has changed the default Python configuration.

Presently, the only problem I am facing is that I can't take print-outs off my system, but with Python not working, maybe the problems will only keep on adding. I suppose the easiest way back to normalcy is to reinstall ubuntu all over again, but I fear I will have to take a backup of all my files and settings and put in atleast 2 hours such that everything works okay.

Any possibility of a repair?? Please help.

---

