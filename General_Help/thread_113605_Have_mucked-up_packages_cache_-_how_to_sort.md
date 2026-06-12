---
title: "Have mucked-up packages cache - how to sort?"
date: 2006-01-06
forum: General Help
---

### Post by andyfg on 2006-01-06
Attempted to install JRE plugin to mozilla the other day, but have only succeeded in locking up the packages cache.

When i attempt to install / uninstall any package using synaptic package manager or apt-get via terminal - I get the following message.

"The package jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory"

Is this terminal - and do I need to re-install the operating system, or has anyone an idea as to how it can be fixed.??

Any solutions would be gratefully appreciated.:(

---

### Post by feathers on 2006-01-08
Try running sudo apt-get remove --purge jre in the konsole. Does it do it and if not what does it say?

---

### Post by kcjameson on 2006-10-20
i have the same problem, different package.
i typed that and got this:

Reading package lists... Done
Building dependency tree... Done
E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.

any ideas?

---

### Post by metalheart on 2006-10-20
Download package from

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fnon-free%2Fs%2Fsun-java5%2Fsun-java5-bin_1.5.0-08-1_i386.deb&md5sum=9c354914dd6dac3257cc499742ef2128&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fnon-free%2Fs%2Fsun-java5%2Fsun-java5-bin_1.5.0-08-1_i386.deb&md5sum=9c354914dd6dac3257cc499742ef2128&arch=i386&type=main)

Then
```
dpkg -i sun-java5-bin_1.5.0-08-1_i386.deb
```

---

### Post by jpmrblood on 2006-10-20
It's likely when you run apt-get, process is interrupted. Try this:

```
#> sudo rm /var/lib/dpkg/archives/lock 
```
```
#> sudo touch /var/lib/dpkg/archives/lock 
```
```
#> sudo dpkg --configure -a 
```
```
#> sudo apt-get remove sun-java5-jre 
```
```
#> sudo apt-get install sun-java5-jre 
```

The idea is to remove dpkg's lock that was never released, try to run any unfinished install session and reinstall the SUN's java package. Btw, within the SUN's java there are  Java Webstart and moz plugin.

---

