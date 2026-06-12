---
title: "move command"
date: 2006-05-04
forum: Desktop Environments
---

### Post by azray on 2006-05-04
Can't seem to find the correct syntax to move default settings for Firefox that I saved on the Desktop in a file called ffsettings. target dir should be /opt/firefox/defaults/profile. Error msg is permission denied.

---

### Post by Ramses de Norre on 2006-05-04
Use sudo;)

```
sudo mv ~/Desktop/ffsettings/* /opt/firefox/defaults/profile
``` (I think this will do what you want, but I'm not totally sure how you want the files in the target dir. This will place them all there without the dir they were in.)

---

### Post by azray on 2006-05-04
tried and got

mv: cannot stat `/home/rgreeves/Desktop/ffsettings/*':

---

### Post by Ramses de Norre on 2006-05-04
Oh I see it's a file, ```
sudo mv ~/Desktop/ffsettings /opt/firefox/defaults/profile/
```
I thought it was a folder, didn't read closely enough.

---

### Post by azray on 2006-05-04
Can't win for losing...

mv: cannot stat `/home/rgreeves/Desktop/ffsettings': No such file or directory
rgreeves@c-71-226-41-138reeveshome:~/Desktop$

---

### Post by Ramses de Norre on 2006-05-04
Are you sure the file is there and you've got the whole correct name? (case sensitive!).
Check with ls ~/Desktop

---

