---
title: "HD over filled"
date: 2006-08-04
forum: Desktop Environments
---

### Post by docetes on 2006-08-04
i have filled my HD to capacity and can't log in!!!!!! Any work around?

---

### Post by Najand on 2006-08-04
Why not using Live CD to erase the unnecessory data on you HD?

---

### Post by docetes on 2006-08-04
i tried that but i can't seem to find any of my files when i use the live cd. I saved everything to the desktop

---

### Post by Ramses de Norre on 2006-08-04
Log into recovery mode and use rm to clear some files.

---

### Post by Geomas on 2006-08-04
I just encountered a similar problem. As Ramses de Norre suggested, you can start Ubuntu in recovery mode (NOT with the Live CD). This logs you in as root. At the prompt or bash, you can type startx to switch to a graphic user interface. Select files to delete (all my files suitable for deletion were in the /home/<my_user_name> directory). Then *empty the trash.* Then re-boot. I hope this helps!

---

### Post by docetes on 2006-08-05
yup the recovery thing worked perfectly. Cheers

---

