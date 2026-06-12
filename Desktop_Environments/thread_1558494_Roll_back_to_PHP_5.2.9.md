---
title: "Roll back to PHP 5.2.9"
date: 2010-08-22
forum: Desktop Environments
---

### Post by everynameistaken1567 on 2010-08-22
When upgraded to 10.4 it appears that PHP also upgrade to 5.3.2  Is there any way to roll PHP back to 5.2.9?

---

### Post by clrg on 2010-08-22
Remove PHP, download a DPKG with the version you want, and install it.

---

### Post by everynameistaken1567 on 2010-08-22
Thanks, but how do I remove PHP and where do I go to download a DPKG?

---

### Post by clrg on 2010-08-22
Remove php:
```
sudo apt-get remove php5*
```

Download php:
```
firefox http://www.google.com/
```

Install php:
```
sudo dpkg -i <downloaded php dpkg file>
```

---

