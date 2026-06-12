---
title: "shutdown causes restart instead"
date: 2009-02-16
forum: General Help
---

### Post by fti100 on 2009-02-16
I'm a complete newbie -  just installed Ubuntu 8.10 32 bit on a Toshiba Satellite U405D laptop (dual boot with vista).  Whenever I try to shutdown (from system menu or clicking on icon on far top right), the computer always restarts.  All the other options (restart, suspend, hibernate) seem to work ok.

When I try "sudo shutdown -h now" or "sudo poweroff" from the terminal, it also causes a restart.

I'd appreciate any advice anyone can offer.  Thanks!

---

### Post by mikewu on 2009-02-17
Not particularly sure why it would be rebooting, but sudo shutdown -h gives the system a choice of halting or powering off.

Trying running 

```
sudo shutdown -P now
```

That only gives the system the option of powering down after being brought down.

Hope this helps!

---

