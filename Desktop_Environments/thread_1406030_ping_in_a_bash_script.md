---
title: "ping in a bash script"
date: 2010-02-13
forum: Desktop Environments
---

### Post by bluethundr on 2010-02-13
Hello,

 I would like to setup a ping test in one of my bash scripts. But *nix pings are continuous which would make the script continue until interrupted with Ctrl+C

 How do you specify a certain number of pings to be issued?

***ah!!!
ping -c $IPADDR

nm.. figured it out.. :)

---

### Post by linux4me on 2010-02-13
Yes, but you need an integer for the number of pings after the "-c" flag. For example, if you want to do three pings it would be:
```
ping -c 3 $IPADDR
```

---

