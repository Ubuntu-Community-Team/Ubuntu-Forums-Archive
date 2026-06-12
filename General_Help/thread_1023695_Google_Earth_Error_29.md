---
title: "Google Earth Error 29"
date: 2008-12-28
forum: General Help
---

### Post by ChrisB111 on 2008-12-28
I have been looking at this [thread]("http://ubuntuforums.org/showthread.php?t=244343&page=2") to fix the google earth startup error. I have tried installing the lib32nss-mdns package but I cant find it, I have the universe repository where it is though. I have also tried ruining it as root. Has anyone else had this problem and worked out how to fix it?

Thanks,

Chris

```

chris@chris-desktop:~$ sudo apt-get install lib32nss-mdns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32nss-mdns

```

---

### Post by oldos2er on 2008-12-28
Try running this command:

 sudo apt-get update && sudo apt-get install lib32nss-mdns

---

### Post by tanush on 2009-11-03
stiull doesnt work

---

