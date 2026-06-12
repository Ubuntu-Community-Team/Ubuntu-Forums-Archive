---
title: "upgrade to 11.04"
date: 2011-05-03
forum: Desktop Environments
---

### Post by bjlockie on 2011-05-03
How do I get an empty desktop?
I upgraded to 11.04 and there is a launcher on the desktop.

I also want my autologin back.

---

### Post by SteveDee on 2011-05-03
> **bjlockie said:**
> How do I get an empty desktop?...

Assuming you are talking about Lubuntu 11.04...try deleting it from the desktop folder via file manager.

> ...I also want my autologin back.

Open file: /etc/xdg/lubuntu/lxdm/lxdm.conf as root and add at the beginning:-
```

autologin=bjlockie

```
...or whatever your username is.

---

### Post by bjlockie on 2011-05-04
I got the autologin to work but isn't there an easier way than editing the file?

The autologin got rid of the panel on my desktop that had shortcuts to run apps.
At least it is gone this boot.
I just wanted to run anything from the menu. :-)

---

### Post by SteveDee on 2011-05-05
> **bjlockie said:**
> I got the autologin to work but isn't there an easier way than editing the file?...

Lubuntu is a very light Linux distribution, and this is achieved by leaving out things like menu editors.

Think of Ubuntu, Lubuntu, Kubuntu & so on as just Linux distro templates. You can add/remove apps and even turn Lubuntu into Ubuntu ([http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)). You just need to decide on the feature/bloat compromise that best suits your needs.

---

