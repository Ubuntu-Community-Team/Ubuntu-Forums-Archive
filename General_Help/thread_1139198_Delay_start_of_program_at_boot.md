---
title: "Delay start of program at boot"
date: 2009-04-26
forum: General Help
---

### Post by fusa on 2009-04-26
I am running an IRC server, and after installing 9.04 my eggdrop bot is loading before services, resulting in the bot not being able to identify properly with the services.  Is there anyway to delay eggdrop so that ircservices is loaded first?

---

### Post by lovinglinux on 2009-04-26
You can create a script using th sleep command before what you want to delay:

```
ircservices
sleep 30 &&
eggdrop
```

---

