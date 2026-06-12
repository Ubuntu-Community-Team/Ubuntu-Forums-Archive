---
title: "Recommendations for developers desktop"
date: 2012-05-10
forum: Desktop Environments
---

### Post by NigelRen on 2012-05-10
I'm going to finish the hardware upgrades to my desktop machine over the weekend and so will be re-installing Ubuntu.  I currently use 11.10 & Gnome, I was wondering if I should install 12.04 and get used to Unity. So I was interested if there are any benefits/drawbacks?

I tend to use Eclipse 4.1 for development with Virtual Machine Manager to manage/run several different types of KVM virtual machines ( both local and remote ).  I also use dual screen ( using NVidia ) a lot!

Would also be interested to hear if I could get NUMA to work as well (dual processors )- but not essential.

---

### Post by codemaniac on 2012-05-10
you should not have any issues running Eclipse or other develepomnet environmnet in 12.04 .
Still you need to get the updated pathes and upgrades at regular basis in order to have a smooth and secure ride .

---

### Post by lukeiamyourfather on 2012-05-10
I'd go for 12.04 LTS at this point because it has support for considerably longer than 11.10 (18 months versus 5 years). If you want to continue using GNOME it can be installed after the fact.

```
sudo apt-get install gnome-shell
```

The hardware like the Nvidia graphics card should be supported just fine. The Linux kernel has supported NUMA hardware for many years. Not sure what version of Eclipse is in 12.04 LTS though.

---

