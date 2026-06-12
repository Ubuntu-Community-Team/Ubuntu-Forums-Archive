---
title: "Changing permissions to the /var/www folder"
date: 2009-02-22
forum: General Help
---

### Post by mharvey87 on 2009-02-22
I want to change sudo permissions to that directory so I don't have to sudo textfiles in it. That is the main directory I am using to create webpages.
Don't respond with anything like telling me to use a different directory or something like that please.

---

### Post by spiderbatdad on 2009-02-22
```
sudo chmod -R 777 /var/www/
```

---

### Post by mharvey87 on 2009-02-22
Thanks, I probably should have tried that first.

---

