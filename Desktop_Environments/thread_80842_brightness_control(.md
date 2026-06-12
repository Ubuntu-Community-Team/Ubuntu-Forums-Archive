---
title: "brightness control??:("
date: 2005-10-23
forum: Desktop Environments
---

### Post by erez1012 on 2005-10-23
the brightness in my mac i book is very high
how can i change thet???
thanks

---

### Post by Ampersand on 2005-10-23
The xgamma command might help. Try going to a terminal and running:
```
xgamma -gamma n
``` 
where n is less than 1 (try about 0.8 or 0.9 to start with).

---

