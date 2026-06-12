---
title: "Problems with updating software"
date: 2008-12-27
forum: General Help
---

### Post by michael91 on 2008-12-27
Every time I try to download stuff from the Update Manager, it comes up with a box saying than an error has occured. The details that it provides are:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

The exact same thing happens when I try to download things from Add/Remove.

I am currently running Ubuntu version 7.10. How would I go about fixing the problem? Would I need to upgrade my version of Ubuntu? Any help would be greatly appreciated.

---

### Post by dcstar on 2008-12-27
> **michael91 said:**
> Every time I try to download stuff from the Update Manager, it comes up with a box saying than an error has occured. The details that it provides are:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
.......

Do what is says:

```
sudo dpkg --configure -a
```

BTW, 7.10 support will end at April 2009.

---

### Post by michael91 on 2008-12-27
So that's what it means. Thanks for the info about when support will finish. I guess that I'll have to upgrade soon, no matter what.

---

### Post by namdung on 2008-12-27
> **michael91 said:**
> So that's what it means. Thanks for the info about when support will finish. I guess that I'll have to upgrade soon, no matter what.

The latest version is Intrepid Ibex 8.10. However, I recommend Hardy Heron LTS, the latest version 8.04.2 coming out on 1/1/2009. Intrepid may have more features but may also have more bugs.

[https://launchpad.net/ubuntu/+milestones](https://launchpad.net/ubuntu/+milestones)
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

