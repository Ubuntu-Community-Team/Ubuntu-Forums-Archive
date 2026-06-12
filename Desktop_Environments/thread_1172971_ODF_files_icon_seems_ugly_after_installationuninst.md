---
title: "ODF files icon seems ugly after installation/uninstallation OOo"
date: 2009-05-29
forum: Desktop Environments
---

### Post by terakinizers on 2009-05-29
Hi all,

   Not a big issue, but looks very bad...

   My current version is 8.04 LTS (Japanese Desktop) and I am using OpenOffice.org 3.1 from PPA-build version (ppa.launchpad.net/openoffice-pkgs/). One day, as the build of l10n'ed version was built too late, I tried to uninstall any previously installed OOo-related packages, and instead, installed packages downloaded from [www.openoffice.org](www.openoffice.org).

   After few days, I returned to PPA-built OpenOffice 3.1 by deleteing packages which were downloaded from openoffice.org. Then, all icons of OOo-related files (*.odt, *.odp and so on) has been changed to the same one with MS-Office files (*.doc, *.ppt, ...).

   I spent about half a day to solve this problem and, by copying icon files to some directories under /usr/share/icons/hicolor, I could manage to resume normal icons as appeared same as before, except one thing.

   Currently, the icons of ODF appeared in "Open File" dialog are really big compared to others. I suppose the dialog uses icons with the 22x22 pixels but the ODF icons are 48x48. Though that makes no problem upon my Ubuntu usage, it looks slightly ugly upon every file opening.

   Does anyone have great ideas to fix this problem?
   Thank you for your comments and suggestions!

JT

---

