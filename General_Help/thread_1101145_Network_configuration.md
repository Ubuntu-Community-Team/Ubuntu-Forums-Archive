---
title: "Network configuration"
date: 2009-03-20
forum: General Help
---

### Post by winiman on 2009-03-20
I am using Ubuntu 8.10 Server with ubuntu-desktop installed.

I try to configure my wire configuration using network-admin but I receive this message:

The configuration could not be saved
You are not allowed to modify the system configuration

What should I do

---

### Post by iaculallad on 2009-03-20
On the terminal:

```
gksudo network-admin
```

---

### Post by winiman on 2009-03-20
Try that the same message. 

Just for your info I am using gnome-network-admin since

---

### Post by iaculallad on 2009-03-20
Try to relate your problem to this [bug filed at launchpad]("https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/188349").

---

