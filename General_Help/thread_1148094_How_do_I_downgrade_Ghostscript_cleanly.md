---
title: "How do I downgrade Ghostscript cleanly?"
date: 2009-05-04
forum: General Help
---

### Post by dwasifar on 2009-05-04
I've found that pdf files created in Jaunty do not display well in Adobe Reader (though they print out fine, and display ok in other viewers).  I suspect that the problem lies in Ghostscript.  Intrepid uses 8.63, Jaunty uses 8.64, and the pdfs produced in Jaunty are missing a lot of control information that was present in the Intrepid ones.

I have a .deb of Ghostscript 8.63 for my architecture, but gdebi will not install it because a later version exists.  If I try to remove the existing version, apt-get tells me it's going to uninstall a whole lot of other stuff in the process:

```
The following packages will be REMOVED:
  bluez-cups cups cups-driver-gutenprint cups-pdf foomatic-db-gutenprint
  foomatic-db-hpijs ghostscript ghostscript-x hal-cups-utils hpijs hpijs-ppds
  hplip hplip-gui ijsgutenprint kde-printer-applet kdeutils kubuntu-desktop
  pnm2ppa splix system-config-printer-kde ubuntu-desktop

``` 

Obviously this seems like something I would rather not do.  Is there a simple way to force the downgrade without this major trauma to the configuration?

---

