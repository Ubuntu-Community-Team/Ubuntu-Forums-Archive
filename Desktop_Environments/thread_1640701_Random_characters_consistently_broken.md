---
title: "Random characters consistently broken"
date: 2010-12-08
forum: Desktop Environments
---

### Post by piccoloprincipe on 2010-12-08
In applications like Firefox or gnome-terminal, some characters get randomly broken. Once the application is running, the broken characters are consistently the same - in the screenshot it is the "t".
This happened after installing Ubuntu NBR 10.04.
I have removed some fonts after installation (like korean, chinese, etc. which I do not use), but I don't think it's related:
```
[11:46:46][giorgio@Tony:~]$ dpkg -l | grep ii | grep ttf
ii  ttf-dejavu-core                       2.31-1                                            Vera font family derivate with additional characters
ii  ttf-freefont                          20090104-7                                        Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-liberation                        1.05.2.20091019-4                                 Fonts with the same metrics as Times, Arial and Courier
ii  ttf-opensymbol                        1:3.2.1-7ubuntu1                                  OpenSymbol TrueType font
ii  ttf-ubuntu-font-family                0.69+ufl-0ubuntu1                                 Ubuntu Font Family, sans-serif typeface hinted for clarity

```

---

### Post by antony_css on 2012-06-01
I also have this problem on my Ubuntu 12.04.

---

