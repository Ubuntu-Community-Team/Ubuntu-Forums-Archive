---
title: "Ventril Server."
date: 2008-09-13
forum: Gaming &amp; Leisure
---

### Post by Pectabyte on 2008-09-13
So I'm trying to run a Ventrilo server on my xubuntu system. I can connect Via LAN but no one externally can connect despite having port forwarded to that system. Any ideas? Limitation of public version of vent server maybe? Also I'f I drag Ventrilo_serv into the terminal it trys to run it but says:"Unable to open configuration file "ventrilo_srv.ini."
ERROR: Unable to read configuration data exiting.
I figure this is a big deal since im runing it by just clicking execute so i have no idea if its even reading the .ini file.

---

### Post by Pectabyte on 2008-09-15
No one has had this problem or knows a solution?

---

### Post by Delfofthebla on 2008-09-16
> **Pectabyte said:**
> No one has had this problem or knows a solution?

I'm still working out making it work better myself, but I had this issue too. I just double clicked the ventrilo_srv, rather than running it through the terminal. Worked fine.

---

### Post by mikewhite on 2008-10-21
What I did was downloaded the vent server for linux.
Extracted the files to a ventrilo folder in my home dir.
Edited the .ini to my server details
Open a terminal box and type ```
 cd /home/account/ventrilo 
```
Then type ```
 ./ventrilo_srv 
```

Then it loaded and ran fine for me and others on the net.

---

