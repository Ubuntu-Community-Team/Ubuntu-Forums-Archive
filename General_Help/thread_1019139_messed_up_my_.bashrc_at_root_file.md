---
title: "messed up my .bashrc at root file"
date: 2008-12-22
forum: General Help
---

### Post by hockeyhead019 on 2008-12-22
ok so i was atempting to edit the bashrc file to install the psptoolchain and i ended up messing it up so that the ONLY path for the root is to the PSPDEV files which i attmepted to set up... so i found the bashrc file in the root directory and tried to fix it manually and i know exactly which lines to remove but it won't let me save it... it says "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." anybody know how a way around this? 

thanks,
hockeyhead

---

### Post by taurus on 2008-12-22
```
gksudo gedit /root/.bashrc
```

---

### Post by hockeyhead019 on 2008-12-22
worked like a charm thanks

---

