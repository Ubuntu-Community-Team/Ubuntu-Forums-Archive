---
title: "fglrx problems"
date: 2005-12-01
forum: Desktop Environments
---

### Post by SnackPack on 2005-12-01
I downloaded the fglrx_6_8_0-9.19.10-1.i386.rpm from [the ati-website]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300"), and tried running it through rpm, which did not work. I followd the instruction to run it through alien, and this made a partial install, wich my package manager is unable to remove (I'm using kpackage). 
It won't let me do any new installs until the fglrx-install is repaired. How do i do this? Is there a .deb-package of the fglrx to be found anywhere?

---

### Post by daller on 2005-12-01
[QUOTE=SnackPack]I downloaded the fglrx_6_8_0-9.19.10-1.i386.rpm from [the ati-website]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300"), and tried running it through rpm, which did not work. I followd the instruction to run it through alien, and this made a partial install, wich my package manager is unable to remove (I'm using kpackage). 
It won't let me do any new installs until the fglrx-install is repaired. How do i do this? Is there a .deb-package of the fglrx to be found anywhere?[/QUOTE]

First of all, to let you install anything again, run this from konsole:

```
sudo apt-get -f install
```

Now that should be solved!

How did you convert the rpm into a deb?

The correct way is:

```
alien --to-deb  fglrx*.rpm
```

Afterwards you should try to install it from konsole (gives better output, I think - Never used kpackage though)

```
dpkg -i fglrx*.deb
```

Hope it works for you!

---

