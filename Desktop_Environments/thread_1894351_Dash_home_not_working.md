---
title: "Dash home not working"
date: 2011-12-12
forum: Desktop Environments
---

### Post by forsubhi on 2011-12-12
when I click Dash home and choose more application then no thing appear 
what is the problem
could I have to reinstall Dash home and how ?

---

### Post by Frogs Hair on 2011-12-12
You could try the following command . ```
unity --reset-icons
```
That will reset all icons to default and if that fails reset Unity .```
unity --reset
```

---

### Post by forsubhi on 2011-12-12
I try then but no thing happen

---

### Post by Frogs Hair on 2011-12-12
Try the following command and restart .```
sudo apt-get install --reinstall dash
```

---

### Post by vgad on 2012-05-08
Thanks, the unity --reset-icons worked perfectly for me and my dash is now working just fine. Don't know about the other options, didn't need to work my way down them. Think this problem can be treated as solved.

---

