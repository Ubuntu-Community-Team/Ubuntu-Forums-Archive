---
title: "Gimp won't update to 2.6.5"
date: 2009-03-09
forum: General Help
---

### Post by Tony_photoplus on 2009-03-09
I have deleted and removed Gimp 2.6.1 so many times and tried to update to the new 2.6.5.  I have done the apt-get install gimp when I have deleted gimp from the packages.  Any way to over come this?

Thanks

Tony

---

### Post by C-- on 2009-03-09
> **Tony_photoplus said:**
> I have deleted and removed Gimp 2.6.1 so many times and tried to update to the new 2.6.5.  I have done the apt-get install gimp when I have deleted gimp from the packages.  Any way to over come this?

Thanks

Tony

Sometimes very new versions of packages take time to get into the repository. In that case you could compile from source, but if you do make sure to archive the source so when  you want to uninstall you can do a 

```
make uninstall
```

to remove the data, as when you compile from source apt-get doesn't keep track of it.

You could also see if someone made a .deb of 2.6.5, download and install with apt-get.

Otherwise you could just wait until the repository is updated.

---

### Post by fragos on 2009-03-09
I'd give [http://getdeb.net](http://getdeb.net) a try search for Gimp and they'll present you with the binaries for a number of Gimp release. These deb packages are built for Ubuntu. I usually download and place them in a folder of their own before opening a terminal with it as the PWD and running "dpkg -i *". Getdeb keeps up with the latest Gimp releases and other goodies.

---

