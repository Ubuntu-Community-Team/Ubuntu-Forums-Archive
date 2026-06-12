---
title: "Uninstalling Beryl?"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by xflatlinex on 2007-04-25
Can someone please assist me with uninstalling Beryl and Beryl Manager?
Thanks

---

### Post by Gillingham on 2007-04-25
If using ubuntu (gnome), go to synaptic, search for packages with beryl or emerald in the name and mark for removal or complete removal.  Not sure what the equivalent package manager for kubuntu is. 

 I'm not familiar enough with using apt from the command line to tell you what the commands are.

Or just to stop using beryl remove beryl-manager from the start up programs.

---

### Post by Waappu on 2007-04-25
Hi

Completly uninstall beryl type in terminal```
sudo aptitude remove --purge-unused beryl emerald emerald-themes
sudo aptitude remove --purge-unused beryl-plugins-unsupported
sudo aptitude autoclean
rm -r ~/.beryl
rm -r ~/.emerald
rm ~/.beryl-managerrc
```

---

