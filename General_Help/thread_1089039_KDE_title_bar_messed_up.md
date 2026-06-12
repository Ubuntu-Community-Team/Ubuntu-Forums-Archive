---
title: "KDE title bar messed up"
date: 2009-03-06
forum: General Help
---

### Post by bobmatino17 on 2009-03-06
well i decided to start using KDE4.2 again and to my dismay the title bar was this ugly blue thing, i tried installing different themes and try them to see if they work(all of them) and still, i get this ugly blue bar! somebody help me please!!!!!!!!!!!

---

### Post by martrn on 2009-03-06
Make sure you have all the correct fonts installed.
```

sudo apt-get install ttf-gentium
sudo apt-get install ttf-dustin
sudo apt-get install ttf-georgewilliams
sudo apt-get install sun-java6-fonts
sudo apt-get install ttf-larabie-deco
sudo apt-get install ttf-larabie-straight
sudo apt-get install ttf-larabie-uncommon

```

To make the available and the ms-fonts use:
```

sudo apt-get install msttcorefonts
sudo fc-cache -fv

```

---

### Post by bobmatino17 on 2009-03-13
i installed the fonts

---

### Post by bobmatino17 on 2009-03-23
bump

---

