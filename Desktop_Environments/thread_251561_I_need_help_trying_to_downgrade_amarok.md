---
title: "I need help trying to downgrade amarok"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Second_Player on 2006-09-05
theres a bug on the ppc version i guess and i'm not really sure how to downgrade anything, but i would like to get it working again, at least untill the bug is fixed.  any help would be much appreciated.

---

### Post by ciscosurfer on 2006-09-05
Go to your /var/cache/apt/archives directory, search for a previous verison of amarok, noting the exact name of the file.  Then remove amarok at the command-line with```
sudo aptitude remove amarok
```Now, type the old file name in the terminal to get your old verison back```
sudo aptitude install amarok(old_version_numbers)
```You can also try to do this with 'dpkg' like so```
sudo dpkg -r amarok
```Then, reinstall the older version```
sudo dpkg -i amarok(old_version_number_here)
```

---

### Post by Skia_42 on 2006-09-05
I encountered the same issue, I tried to downgrade to 1.3 but it is still not working. Does anyone know what the previous version was nad how you put it into the terminal e.g. amarok(1.3.9) or amarok1.3.9 ?
NM, I got it working. My version numbers was 1.2 not 1.3.9

---

### Post by Second_Player on 2006-09-05
thank you very much, i actually didnt have to reinstall the old version, when i got rid of the new one it automaticly installed the previous one, thank you so much.

---

