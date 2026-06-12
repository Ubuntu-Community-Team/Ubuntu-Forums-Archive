---
title: "Request for information"
date: 2009-03-24
forum: General Help
---

### Post by zimar1 on 2009-03-24
Will Ubuntu support a HP Workstation XW8000 with dual xeon 3.06 GHz cpu's and 6 GB of memory?

Thanks for your help.

Zimar

---

### Post by dcstar on 2009-03-24
> **zimar1 said:**
> Will Ubuntu support a HP Workstation XW8000 with dual xeon 3.06 GHz cpu's and 6 GB of memory?


Get a Live CD and see for yourself - that is what they are for.

---

### Post by mb_webguy on 2009-03-24
> **zimar1 said:**
> Will Ubuntu support a HP Workstation XW8000 with dual xeon 3.06 GHz cpu's and 6 GB of memory?

Thanks for your help.

Zimar

Based purely on that description, it *should*, but a computer is a lot more than just a processor and memory.  It's possible that there is some odd or very new bit of hardware for which no Linux drivers have been written yet.  

Generally, the problem areas tend to be video cards and wireless networking cards.  nVidia video cards are fairly well-supported, while ATI cards can occasionally be problematic.  Wireless cards are hit-or-miss depending on the chipset.  Even if they aren't natively supported, however, you can generally still get them to work using ndiswrapper and the Windows driver.

---

### Post by spcwingo on 2009-03-24
I think the server kernel supports this.  Try installing the server edition and if you would like the standard desktop just run this command:

```
sudo apt-get install ubuntu-desktop
```

---

