---
title: "problems with ubuntu-netbook-remix"
date: 2010-04-04
forum: Desktop Environments
---

### Post by donmatas on 2010-04-04
Hello
I have install the netbook-launcher applet in a toshiba netbook (nb200) with karmic (it was impossible to install directy unr 9.10 in this machine). The problem is than sometimes the applet doesnt runs at the begging and if I try to make it run it wont.

could any one help me to solve this problem?

thanks

DM

---

### Post by donmatas on 2010-04-04
> **donmatas said:**
> Hello
I have install the netbook-launcher applet in a toshiba netbook (nb200) with karmic (it was impossible to install directy unr 9.10 in this machine). The problem is than sometimes the applet doesnt runs at the begging and if I try to make it run it wont.

could any one help me to solve this problem?

thanks

DM

I solved it purging the ubuntu-desktop and installing  netbook-launcher ubuntu-netbook-remix

```
sudo apt-get install netbook-launcher ubuntu-netbook-remix
```

reboot

```
sudo apt-get purge ubuntu-desktop
```

reboot

---

