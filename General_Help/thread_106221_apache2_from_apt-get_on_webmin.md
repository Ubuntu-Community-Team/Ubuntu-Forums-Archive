---
title: "apache2 from apt-get on webmin"
date: 2005-12-20
forum: General Help
---

### Post by davebradford on 2005-12-20
can anybody help me to configure webmin using the apache2 deamon from apt-get??

---

### Post by davebradford on 2005-12-20
no-one else had this problem?

---

### Post by davebradford on 2005-12-20
or any experts here?

---

### Post by adie273 on 2005-12-20
do you mean getting Webmin to work with Apache2?

If so I had the same problem. The default settings in Webmin aren't for Apache2. If you goto the Apache module in Webmin and change the settings, it gives a number of settings for file locations. and the folders those files are in are all say 'apache'. I think all you need to do is change them to 'apache2' instead. (If that makes sense)

Think thats what I did and it worked fine. Although I can't be absolutely certain because i'm not at my own computer to check. But take a look in the Webmin apache settings and you should see what I mean. Its easy enough to sort.

Hope it helps anyway, good luck.

Adie

---

### Post by davebradford on 2005-12-22
ah yes your very right once in the module conf u can chage all the paths..

---

