---
title: "synaptic problem"
date: 2005-04-23
forum: Desktop Environments
---

### Post by mdm4301 on 2005-04-23
I am a new linux user and am having a problem with synaptic.  When I start it, it says that I have a broken package that needs to be fixed.  So I click on the fix broken packages option and then click apply.  Everything seems to be going ok but at the end it gives me the following error message:

E: /var/cache/apt/archives/kdelibs-data_40x1.af2300000005ap-8893.4.0-0ubuntu3.1_all.deb:  trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

What do I need to do to fix this?  Thanks for the help.

---

### Post by XDevHald on 2005-04-23
You'll need to **apt-get install knetworkconf **to get this package running, if you don't have it, which you might, but double check. If you do have this package, reinstall it.

Then try again with the Synaptic broken package.

If I am wrong, don't schun me ;)

---

### Post by mdm4301 on 2005-04-24
thanks for the suggestion but Im still getting the same problem

---

### Post by dangerous666 on 2005-09-07
[QUOTE=mdm4301]thanks for the suggestion but Im still getting the same problem[/QUOTE]
same here..  :roll:

---

### Post by Gezzer on 2005-09-07
[QUOTE=][/QUOTE]
 via synaptic uninstall knetworkconf

do your upgrades

reinstall knetworkconf

---

