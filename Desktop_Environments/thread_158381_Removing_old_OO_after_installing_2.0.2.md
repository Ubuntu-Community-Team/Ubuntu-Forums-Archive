---
title: "Removing old OO after installing 2.0.2"
date: 2006-04-11
forum: Desktop Environments
---

### Post by rowck001 on 2006-04-11
I have downloaded the debs for OpenOffice 2.0.2 and installed - I now have the new version working (via editing the ooo-wrapper file - thanks to the posters here for that help) but if I want to remove the old version via synaptic - it says I must also remove ubuntu-desktop package as well.

I read in another thread - "dont panic it doesnt mean what you think it means". I take this to mean it wont screw ubuntu to remove ubuntu-desktop but I just want to check this is OK before doing this as I have a beautiful system working at the moment and dont want to mess with it.

If it is OK to remove ubuntu-desktop, what is its purpose?

---

### Post by Sutekh on 2006-04-11
Have a read

[Ubuntu Packages - ubuntu-desktop](http://packages.ubuntu.com/breezy/base/ubuntu-desktop)

Ubuntu-desktop is a 'meta-package' that depends on a lot of other files.  So installing it with apt-get pulls in all those files as dependant packages.  The ubuntu-desktop package itself contains nothing of value.

It is worthwhile keeping it installed for when installing other packages that may depend on those packages installed by ubuntu-desktop, thus depending on ubuntu-desktop being installed.

However because ubuntu-desktop depends on the vesion of OpenOffice in the Ubuntu repositories (the old one) and not the one you installed separately, means that if you try to re-install ubuntu-desktop means that you try to re-install the old OpenOffice.  

So leave ubuntu-desktop uninstalled, unless you plan to dist-upgrade to dapper, in that case make sure you have ubuntu-desktop installed before dist-upgrading.

---

