---
title: "Disabled GDM and now cant mount external hdd."
date: 2008-12-10
forum: General Help
---

### Post by citizenchris099 on 2008-12-10
ok here goes. I disabled the GDM service through the gui tool (unchecked it) 

created a .xinitrc that reads as follows

#!/bin/sh 

# Start the Fluxbox Window Manager 
exec /usr/bin/startfluxbox 

so now I use startx to get into my gui (fluxbox) and it works fine. Only one problem ...I have two Western Digital "My Book" 500gb external hdd (formated fat32) connected via USB. Mind you these drives have always mounted/worked fine. Immediately after making the above mentioned changes (disable GDM etc...) my drives wont mount...the two icons for the drives appear in thunar but when I click them (this usually mounts them) i get a sort of permission error. Again this problem began immediately after disabling GDM.

---

### Post by citizenchris099 on 2008-12-10
any ideas? at this point im willing to re-install. was trying to avoid this though for obvious reasons.

---

