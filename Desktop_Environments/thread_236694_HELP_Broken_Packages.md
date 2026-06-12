---
title: "HELP: Broken Packages"
date: 2006-08-15
forum: Desktop Environments
---

### Post by MiniJames on 2006-08-15
I was trying to install a developer version of gobby. To meet the dependancies I upgraded several packages. I am now presented with the following error:

```
james@kami:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  libatk1.0-0: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
  libatk1.0-dev: Depends: libatk1.0-0 (= 1.11.4-0ubuntu1) but 1.12.1-1 is installed
E: Unmet dependencies. Try using -f.
james@kami:~$
```

When I run ```
apt-get -f install
``` I get the following (very scary) output:

[http://paste.getlinuxhelp.org/2644](http://paste.getlinuxhelp.org/2644)

Which I promptly abort. What should I do to fix the broken packages?

Thank in advance for your help!

---

### Post by rudiz on 2006-08-15
Go to synaptic and in te File or in Edit >Fix broken packages

---

### Post by rudiz on 2006-08-15
And install the app with synaptic. ;-)

---

### Post by Ramses de Norre on 2006-08-15
> I was trying to install a developer version of gobby. To meet the dependancies I upgraded several packages.
I'm afraid we'll have to conclude that ubuntu and the package you want to install aren't compatible.. The ubuntu packages need older libs then the gobby package and don't work with the new ones. 
Unless you find a workaround I think you'll need to give up using this on ubuntu.

And to fix your problems with apt: Open synaptic, select the packages you upgraded, open the package menu, do force version and pick the original dapper version.

---

### Post by MiniJames on 2006-08-16
> **rudiz said:**
> Go to synaptic and in te File or in Edit >Fix broken packages

Rudiz, thats exactly what ```
apt-get -f install
``` does :/. If you do that it attempts to delete every package on my system.

However, using synaptic. I was able to force the old version and everything is now working again :razz:. Thanks Ramses!

<Problem Solved>

---

