---
title: "[SOLVED] How can I remove certain TTF fonts?"
date: 2008-08-28
forum: Desktop Environments
---

### Post by d0nut on 2008-08-28
I installed a couple of TTF that I dont want anymore.  When I go to usr/share/fonts/truetype, I see the fonts I want to delete but I get an error saying I don't haver permission.  How do I get permission to remove the fonts from this folder (what steps do I take).  Thanks!

---

### Post by silkstone on 2008-08-28
Alt-F2 and enter...

gksudo nautilus

Then navigate to the fonts folder and delete the ones you don't want. Then, to refresh the fonts cache, open a terminal and...

sudo fc-cache -f

Please be very careful when using Nautilus as root - don't delete or alter anything you are unsure of!

---

### Post by d0nut on 2008-08-28
Thank you very much SilkStone.

---

