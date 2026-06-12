---
title: "Correct icon for HP LaserJet m1536dnf MFP (printer) in HPLIP Status Service"
date: 2011-06-01
forum: Desktop Environments
---

### Post by Dondermans on 2011-06-01
I recently installed a HP LaserJet m1536dnf MFP. I noticed that the HP Device Manager Version 15.0 (bundled with HPLIP 3.11.5) shows the correct printer name, but uses a HP LaserJet m1522 icon:

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/HP_LaserJet_m1522_backup.png[/IMG]

Upon browsing the /usr/share/hplip/data/images/devices/ directory, I did not find an icon for the HP LaserJet m1536dnf MFP. Hence I replaced the icon with the correct icon (please find it attached).

To allow the Device Manager to call the correct image I had to rename the file I created to 'HP_LaserJet_m1522'.

To use this icon:
1. close HPLIP Status Service
2. press 'alt F2' to bring up the 'run application' window
3. enter 'gksu nautilus'
4. navigate to /usr/share/hplip/data/images/devices/
5. find HP_LaserJet_m1522.png
6. rename the file you found to HP_LaserJet_m1522_backup.png (as long as you do not connect a m1522 *and* a m1536dnf MFP at the same time, you should be fine)
7. paste the attached image
8. restart HPLIP Status Service

PS. I attached the icon, because Photobucket tends to change the image properties.

---

