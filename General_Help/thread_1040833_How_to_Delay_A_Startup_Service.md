---
title: "How to Delay A Startup Service?"
date: 2009-01-15
forum: General Help
---

### Post by bsalt on 2009-01-15
Hey guys,

I have a random what-if? question that comes to mind. I know this is possible in Vista (and if it is in Vista, then it has to be in Ubuntu ;)), but how can I specify a service to startup "delayed" when I start up Ubuntu? I have an Ubuntu workstation that runs VMWare, MySQL, JungleDisk online backup, TimeVault, etc, and I don't necessarily need all of my applications and services to try to start at the same time. I just want to get connected to wireless first, and then I'll worry about my virtual machines and database server.

Any ideas? I think I have seen this before, but I can't seem to find the instructions on how to do this.




Thanks guys,
Jonathan

---

### Post by edmondt on 2009-02-08
I'd like to know too :) That will go towards speeding up boot time :)

---

### Post by dcstar on 2009-02-08
> **bsalt said:**
> Hey guys,

I have a random what-if? question that comes to mind. I know this is possible in Vista (and if it is in Vista, then it has to be in Ubuntu ;)), but how can I specify a service to startup "delayed" when I start up Ubuntu? I have an Ubuntu workstation that runs VMWare, MySQL, JungleDisk online backup, TimeVault, etc, and I don't necessarily need all of my applications and services to try to start at the same time. I just want to get connected to wireless first, and then I'll worry about my virtual machines and database server.
.......

All system services are started in numerical order in /etc/rc2.d, if you want things to commence later then change the name so it has a higher number.

I also suggest reading this:

[http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by warp99 on 2009-02-08
You can use update-rc.d to change or remove system service links. You could remove the startup runlevels, but leave the shutdown ones with something like this:

```
sudo update-rc.d -f vmware remove
sudo update-rc.d vmware stop 20 0 6 .
```

This way you can start the services manually or with a script as needed and still have the system shut them down. The man pages for update-rc.d has some more detailed examples.

---

