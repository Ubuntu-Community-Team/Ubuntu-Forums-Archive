---
title: "Unwanted Nautilus in Kubuntu"
date: 2008-11-28
forum: Desktop Environments
---

### Post by MartinG on 2008-11-28
I have Intrepid installed, both Ubuntu and Kubuntu, and in Kubuntu/KDE4 I keep getting Nautilus open up when I want Dolphin (or Konqueror).  This happens with the New Device notifier if I click on "Open with Dolphin", with Smb4k if I click on "Open with Konqueror", and with Firefox if I click on "Open containing folder" after a download.

Nothing against Nautilus as such, but I'd really rather use the KDE apps on a KDE desktop.  I can't find anything helpful in System Settings under File Associations.

---

### Post by Farmer of Bricks on 2008-11-30
This worked for me:

1. Open "System Settings"
2. Click on the "Advanced" tab
3. Click on "File Associations"
4. In the "Find file type or filename pattern" box, type "directory", sans quotes
5. Click on "inode" in the box just below the search box.
6. Click on "directory"
7. Under "Application Preference Order", click "Add".
8. In the box at the top, type "/usr/lib/kde4/bin/kfmclient openURL %u inode/directory", sans quotes.
9. Hit "OK"
10. Hit "Apply"

---

