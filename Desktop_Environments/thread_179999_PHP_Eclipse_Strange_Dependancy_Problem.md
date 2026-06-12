---
title: "PHP Eclipse Strange Dependancy Problem"
date: 2006-05-21
forum: Desktop Environments
---

### Post by saurabhnanda on 2006-05-21
Hi,

I was trying to do a manual installation for the PHP Eclipse plugin available at [PHPEclsipe.de]("http://www.phpeclipse.de"). I was following the installation instructions available [here.]("http://www.plog4u.org/index.php/Using_PHPEclipse_:_Installation_:_Installing_PHPEclipse")

After unzipping the zip archive in /usr/share/eclipse, I started the Eclipse IDE with the -clean option as root. I went to Help->Software Updates->Manage Configuration->Show Disabled Features. The five items (Klomp sftp sync support, net.sf.eclipsetidy.feature, Quantum DB, net.sourceforge.phpeclipse, and Subclipse) were not available in the tree menu. The only item available was PHPeclipse 1.1.8 and I enabled it.

After enabling, I checked out the status and there was a huge list of dependancy errors:

```
Plug-in "net.sourceforge.phpdt.smarty.ui" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.core" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.debug.core" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.debug.ui" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.externaltools" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.launching" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.phphelp" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.ui" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.webbrowser" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.xml.core" version "1.1.8" referenced by this feature is missing.

Plug-in "net.sourceforge.phpeclipse.xml.ui" version "1.1.8" referenced by this feature is missing.
```

I'm on Ubuntu Breezy Badger 5.10 -- please can someone help me out with this problem?

TIA
Nandz.

---

