---
title: "How to make shell scripts run at startup?"
date: 2009-01-04
forum: General Help
---

### Post by Zebra_ on 2009-01-04
Any ideas?

---

### Post by Zebra_ on 2009-01-04
bump

---

### Post by adult swim on 2009-01-04
for script named script
make sure your script is executable, chmod 755 script
put it in /etc/init.d
then run sudo update-rc.d script defaults

---

### Post by semi_fiction on 2009-01-04
System->Preferences->Sessions->Startup Programs->Add

Also, don't bump after only 5 minutes =]

---

### Post by MS-Hater on 2010-06-22
> **adult swim said:**
> for script named script
make sure your script is executable, chmod 755 script
put it in /etc/init.d
then run sudo update-rc.d script defaults


Perchance, would that run the script as root? I'm looking into running the shell commands that share my wireless broadband connection with my home network, at boot time. Will your instructions work for that?

---

