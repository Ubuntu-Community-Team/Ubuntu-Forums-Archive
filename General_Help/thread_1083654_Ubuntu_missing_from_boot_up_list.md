---
title: "Ubuntu missing from boot up list"
date: 2009-03-01
forum: General Help
---

### Post by Benbow on 2009-03-01
I have just installed Intrepid but unfortunately it doesn't show on my boot up list and I can't select it. Could anyone point me in the right direction to correct this?

---

### Post by blazemore on 2009-03-01
What does show up on your list?

---

### Post by gabril on 2009-03-01
Do you get a grub menu? If you havnt then probobly your mbr got corruped somwhere, try inserting your ubuntu disk and coose the textbased installer, fast forward to the install grub section.. install grub and reboot and that should have solved your problem.

If you have grub and still it doesnt show ubuntu, you can manually add an entry for ubuntu by pressing "E" and follow the onscreen instructions, google it somewhere, its not hard.

---

### Post by blazemore on 2009-03-01
If you have 2 hard drives, make sure the BIOS is set to boot from the one Ubuntu is on

---

