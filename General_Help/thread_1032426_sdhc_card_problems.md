---
title: "sdhc card problems"
date: 2009-01-06
forum: General Help
---

### Post by mccartryan on 2009-01-06
I just bought a new 4gb sdhc card for my creative zen player.  I had transferred some avi files to it last night then this morning half of them were missing.  They aren't being recognized by either my desktop or the zen itself, but they are still eating up memory on the card.  Does anyone know how I can access these files to delete them.  (They aren't recognized as hidden files either)

---

### Post by redilyn on 2009-01-06
Is it possible to just copy the remaining files to your hdd then format your sdhc card?

Then you could just copy everything back.

---

### Post by mccartryan on 2009-01-06
any suggestions as to how I can go about formatting the SDHC card?  I have installed and opened gparted, but the card is not being recognized by the program.  What other options do I have here?

---

### Post by mccartryan on 2009-01-06
solved my problem:  After I opened gparted with sudo it did recognize the card.  All I really had to do was delete the fat32 partition that already existed and it somehow allowed me to view and ultimately delete those files.  I created a new fat32 partition with gparted and now everything is working perfectly again.  Hopefully it stays that way now.

---

