---
title: "Navini Diagnostics"
date: 2006-01-12
forum: General Help
---

### Post by mosestruong on 2006-01-12
Has anyone been able to install the Navini diagnostic tool ([http://www.navini.com/pages/support/userdownloads.htm](http://www.navini.com/pages/support/userdownloads.htm)) on their Ubuntu system?

I keep getting the following error:
/tmp/install.dir.11357/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I tried to follow the instructions at [http://www.cse.unsw.edu.au/~dons/unwired_openbsd.html#Navini](http://www.cse.unsw.edu.au/~dons/unwired_openbsd.html#Navini)
But that is for RedHat, and it talks about having to install the redhat emul package is installed, and kern.emul.linux sysctl has been set to 1. Does anyone know what this is, and if there's an equivalent in Ubuntu? 

Thanks in advance.

moses

---

### Post by Mr_Grieves on 2006-01-12
[QUOTE=mosestruong]Has anyone been able to install the Navini diagnostic tool ([http://www.navini.com/pages/support/userdownloads.htm](http://www.navini.com/pages/support/userdownloads.htm)) on their Ubuntu system?

I keep getting the following error:
/tmp/install.dir.11357/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I tried to follow the instructions at [http://www.cse.unsw.edu.au/~dons/unwired_openbsd.html#Navini](http://www.cse.unsw.edu.au/~dons/unwired_openbsd.html#Navini)
[/quote]
You seem to be missing a file in the shared libstdc++ and libc6 libraries.. What to do about that I do not know.. I'm not a big fan of installing everything.. just in case.. but I guess you could try that.

> 
But that is for RedHat, and it talks about having to install the redhat emul package is installed, and kern.emul.linux sysctl has been set to 1. Does anyone know what this is, and if there's an equivalent in Ubuntu? 

It means they want you to install some kind of Emulation package.. you need to find that one, or check if you already have it installed.
When you've installed the package you may write this:

```

sudo echo "kern.emul.linux=1" >>/etc/sysctl

```

---

