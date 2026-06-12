---
title: "Creating swap partition after installation"
date: 2006-01-11
forum: General Help
---

### Post by eqisow on 2006-01-11
I didn't create a swap partition when I installed Kubuntu recently. I decided a bit later to go ahead and create one, so I made the linux swap at the end of the drive using qtparted. However, I can't get Kubuntu to use it. Knoppix recognizes and uses the new swap partition perfectly. How do I make Kubuntu realize it's there?

Edit: Also, whenever I click and drag to select something the computer usage jumps to 100% and X becomes laggy until I let go. What's up with this?

---

### Post by eqisow on 2006-01-11
Problem solved, just needed to add ```
/dev/sda3   none      swap    sw                0 0
``` to fstab.

---

