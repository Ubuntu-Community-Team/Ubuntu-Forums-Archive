---
title: "Winter 09 Power Failure...now apt / Synaptic won't work..."
date: 2009-02-01
forum: General Help
---

### Post by ChampAmp on 2009-02-01
After day 4 of no power, its finally back and we're at home again...but, it has had an ill effect on my ubuntu 8.10 desktop. Fsck detected problems, and fixed several things....though now I believe certain files were cooked....when I run synaptic from gui or apt-get from command line, it fails when it reads state information:

```
champamp@DAD:/var/lib/dpkg$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Error!
E: Read error - read (5 Input/output error)
E: Read error - read (5 Input/output error)
```

status and available files in /var/lib/dpkg were incomplete, backup versions (-old) no better....dpkg --configure -a didn't do much other than tell me that my files were screwed up....

Can I re-install from cd the whole dpkg / ap world somehow? Or, am I better off re-installing ubuntu (figuring out how to preserve my data, etc..)

---

