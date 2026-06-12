---
title: "No rc.local how I execute commands on boot"
date: 2006-09-30
forum: Desktop Environments
---

### Post by hraposo on 2006-09-30
I've ubuntu Breeze as server. It have nor the file rc.local. How I put command to begin with the boot of computer? I've no grafic X.

---

### Post by djRobbieF on 2006-09-30
Perhaps drop an sh script to launch the command in /etc/rcS.d

Look at another file from that directory for the formatting.

The S# is the sequence in which the file is run upon boot.

---

