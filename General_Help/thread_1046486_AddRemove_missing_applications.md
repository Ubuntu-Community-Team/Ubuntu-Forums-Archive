---
title: "Add/Remove missing applications"
date: 2009-01-21
forum: General Help
---

### Post by ChrisGaeth on 2009-01-21
I went to my add/remove applications to add something today and it is blank.  I did some google searching but came up with nothing.  Help.

---

### Post by adult swim on 2009-01-21
if you have add/remove open, close it and then go to a terminal, applications>accessories>terminal and paste in ```
sudo apt-get install --reinstall app-install-data app-install-data-commercial
```  then hit enter, type in your password and hit enter.  after it is done, try opening add/remove again

---

### Post by ChrisGaeth on 2009-01-21
That did it.  Thank you.

---

### Post by 2hot6ft2 on 2009-01-21
If you just installed adobe air that's what did it and if you install it again it will do it again.

---

