---
title: "Changing file extnsions?"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Stambo00 on 2005-10-24
I'm currently trying to change all the file extensions in a folder from .ico to .png. Can i do this in with a simple command? Is it even possible?

---

### Post by Pablo_Escobar on 2005-10-24
AFAIK this should help : **mv *.ico *.png**

---

### Post by Stambo00 on 2005-10-24
Could you please give an example, I'm having a little trouble using the command.

---

### Post by Pablo_Escobar on 2005-10-24
1. cd to the directory You have you files in f.e. **cd /home/stambo/Desktop**
2.try different command:
**for f in *.ico; do mv ./"$f" "${f%ico}png"; done**

---

