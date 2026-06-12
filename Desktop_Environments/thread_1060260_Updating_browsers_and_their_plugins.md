---
title: "Updating browsers and their plugins?"
date: 2009-02-04
forum: Desktop Environments
---

### Post by luigi_mb on 2009-02-04
Ubuntu's Canonical repositories are often outdated. For example, Firefox is still at v3.0.5 (but v3.0.6 has been released), Seamonkey at v1.1.12 (but v1.1.14 has been released), Sun Java JDK/JRE at v1.6.0_10 (but v1.6.0_12 has been released), Sylpheed at v2.5.0 (but v2.6.0 has been released), Filezilla at v3.1.2 (but v3.2.0 has been released), etc.  Most of the new versions, among other things, fix security vulnerabilities; in other words updating them is not a luxury, but a necessity. However, the new packages, as released by Mozilla, Sun, etc., are not usually compatible with the Canonical packages: for example, applications are installed in different folders, creating problems with plugins, profiles, etc.. Furthermore, many non-Canonical packages have no uninstaller, and the usual suggestion of simply removing the installation folder often results in bad, unintended consequences. 

Question: what is the best way to proceed?

/luigi_mb

---

### Post by Hooya on 2009-02-04
Do you have backports enabled in your software sources?

Also, for many of those programs there is are maintained repositories that you could add for each one.  It's a pain, I know, but the way that the Ubuntu philosophy for updating software works, nothing upgrades major versions until a new release of Ubuntu.

I'm still on Hardy and find myself adding repositories quite often to keep up with things like OpenOffice, Pidgin, etc.

---

### Post by luigi_mb on 2009-02-06
> **Hooya said:**
> Do you have backports enabled in your software sources?

Also, for many of those programs there is are maintained repositories that you could add for each one.  It's a pain, I know, but the way that the Ubuntu philosophy for updating software works, nothing upgrades major versions until a new release of Ubuntu.

I'm still on Hardy and find myself adding repositories quite often to keep up with things like OpenOffice, Pidgin, etc.

Thank you for the suggestion and for the explanation. Backports do help a little.  I guess I will wait for the new release.

/luigi_mb

---

