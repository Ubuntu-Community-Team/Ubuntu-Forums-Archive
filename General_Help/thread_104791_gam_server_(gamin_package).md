---
title: "gam_server (gamin package)"
date: 2005-12-16
forum: General Help
---

### Post by -DarkMind- on 2005-12-16
this demon consume 550 MB of my memory 

i tried to uninstall but a lot of packages depends on it

how fix this?

i kill the demon with kill -9 

but then start ubuntu start automatic :mad:

---

### Post by christooss on 2005-12-18
```
crontab -e
```
put folowing line in and save
```
1 * * * * killall gam_server
```

It will restart gamin server every hour

---

