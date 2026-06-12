---
title: "root pwd change?"
date: 2005-12-09
forum: General Help
---

### Post by haso on 2005-12-09
I just installed Kubuntu 5.10 from the cd. Everything went fine, even the dual boot with W2k. But.. when I tried sudo, the root pwd was requested. I was not prompted during installation for any root-pwd (or just missed it). How do I change the root pwd. I tried my login pwd, but that failed.
Is there a default root-pwd applied during installation?

any suggestions welcome,

regards
hans

---

### Post by Zaventh on 2005-12-09
Always search the boards before asking questions...

sudo uses your user password as root. Just enter your user's password when sudo'ing.

---

### Post by syncme on 2005-12-09
sudo passwd root

Should allow you to set the password for root.

syncme

---

### Post by frodon on 2005-12-09
You should read that : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)

---

### Post by Rog131 on 2005-12-09
This may help: [http://www.frankandjacq.com/ubuntuguide/5.04/#setchangeenablerootpassword](http://www.frankandjacq.com/ubuntuguide/5.04/#setchangeenablerootpassword)
([http://www.frankandjacq.com/ubuntuguide/5.04/](http://www.frankandjacq.com/ubuntuguide/5.04/))

---

### Post by haso on 2005-12-09
Thank guys,

thanks for the links.
Learned a lot in the few hours I am up and running in the Ubuntu/linux world.
This is encouraging.
Hope to donate my two cents to the Ubuntu world in the near future.

regards,
Hans

---

