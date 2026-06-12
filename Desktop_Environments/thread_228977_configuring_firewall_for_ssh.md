---
title: "configuring firewall for ssh?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by mx2000 on 2006-08-03
Hi!

I want to log into my ubuntu machine using ssh from my windows pc, but all I get is "Connection refused".

I installed firestarter and set "allow ssh (port 22) for everyone", but that doesn't seem to change a thing...

Even when ssh-ing from the linux box itself (ssh localhost) I get "connection refused".

Any help on this would be greatly appreciated.

Thanks
Martin

---

### Post by DarkNemesis618 on 2006-08-03
Is the username added to the ssh group?  Not everyone can ssh into a machine.  Add the user you want to be able to ssh into your box and try again.  You might have to restart the ssh service.  Also make sure you have the ssh server.

I believe it is this.

```
sudo apt-get install openssh-server
```

Hope that helps.

---

### Post by mx2000 on 2006-08-04
You were right, openssh-server wasn't installed :idea: .

It all works now! Thanks! :D

---

### Post by DarkNemesis618 on 2006-08-04
You're welcome, glad i could help.  Let me know if you have any other problems.

---

