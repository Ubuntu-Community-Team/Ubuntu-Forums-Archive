---
title: "cedega permission problem"
date: 2005-09-18
forum: Gaming &amp; Leisure
---

### Post by atad6 on 2005-09-18
hi, i was able to install cedega but when i go to launch an exe file i always get this error

```
wine: '/home/username/.transgaming/wineserver-ubuntu' is not owned by you
``` 

did i do something wrong on install? any help would be great!

Thanks!

---

### Post by xbaez on 2005-09-18
Hello
I made a new poll called:
Point2play And Cedega Problems Go Here - [http://www.ubuntuforums.org/showthread.php?t=66348](http://www.ubuntuforums.org/showthread.php?t=66348)

Please go there since it's usefull to have one poll for all those problems
Check the permissions of that folder, 

chown -vR yourusername:yourmaingroup /home/username/.transgaming

---

