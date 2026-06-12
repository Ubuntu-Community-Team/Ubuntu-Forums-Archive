---
title: "Xubuntu 10.10 Xfce Error when booting"
date: 2010-12-02
forum: Desktop Environments
---

### Post by metallica1973 on 2010-12-02
I just installed a fresh copy of Xubuntu 10.10 on a penstick and everything was working fine at work and at home. Now when I got to the work this morning I connected the stick to my office network and I got this error:

[PHP]Could not look up internet address for localhost.localdomain.
This will prevent Xfce from operating correctly.
It may be possible to correct this problem by 
adding localhost.localdomain to the 
file /etc/hosts on your system[/PHP]

Why did this change if nothing was modified?

---

### Post by metallica1973 on 2010-12-02
I was able to resolve the issue. It turned out to be that somehow the /etc/hosts file was deleted or not present. How that happen from just taking it home from work and connecting it to my network via DHCP, I do not know or understand. Can someone give me some clarification on why this happened?

---

