---
title: "remove program installed without synaptic"
date: 2009-06-12
forum: General Help
---

### Post by hero1900 on 2009-06-12
how to remove program that installed manually (without synaptic)

---

### Post by colau on 2009-06-12
> **hero1900 said:**
> how to remove program that installed manually (without synaptic)
```

sudo apt-get remove <package-name>

```
Or
```

sudo aptitude remove <package-name>

```

---

### Post by LepeKaname on 2009-06-12
use aptitude... (use purge to remove config files as well)

sudo aptitude purge package_name

if that is not what you want.. then do a:

sudo dpkg -L package_name

It will show you all the files installed, so you can manually remove all of them.

---

### Post by dcstar on 2009-06-12
> **hero1900 said:**
> how to remove program that installed manually (without synaptic)

It depends totally on the program you installed and what removal scripts it has.

---

### Post by majamba on 2009-06-12
aptitude tends to do job really well 

so the other suggested

sudo aptitude purge package
sudo aptitude remove package

---

### Post by lamego on 2009-06-12
If you mean programs installed from source, your best choice is to re-install those using checkinstall which will create a .deb package for the installation. 
Then you will be able to remove them using synaptic and apt-get remove.

---

### Post by vahnx on 2009-06-12
I vote for apt-get remove *insert package name* as in you used an apt-get front-end to bring it in, so use apt-get to take it out.

---

### Post by ad_267 on 2009-06-12
The above suggestions won't necessarily work. It depends on how you installed the program. Saying you "manually" installed it doesn't really help. Exactly how did you install it?

---

### Post by BlazeFire247 on 2009-06-12
It really depends on how you installed it, as said by ad_267. 

If you installed it using Add/Remove, use Add/Remove to remove the program. Or, you can use sudo apt-get remove <application name> to remove it.

---

### Post by Soul-Sing on 2009-06-12
> **dcstar said:**
> it depends totally on the program you installed and what removal scripts it has.

+1

---

### Post by t0p on 2009-06-12
If the program cannot be removed through apt-get or aptitude, there is another way.

The command

```
which program_name
```

will return output something like

```
/usr/bin/program_name
```

which means, in this case, that the executable of the app "program_name" is located at /usr/bin/program_name.  So you will be able to navigate to that location and delete the binaries manually (using "sudo" to get admin privileges, of course).  This will not remove config files.

---

### Post by hero1900 on 2009-06-12
i mean that it is not a deb package i install some programs using configurationtion file in the source directory, so how i can remove it
convert it to deb or thier is another way

---

### Post by hero1900 on 2009-06-12
bumb
:popcorn:

---

### Post by mc4man on 2009-06-12
If you compiled the app and still have the source (build) dir. then cd to it and run 

sudo make uninstall

Many, but not all sources will have an uninstall script, if so than you're in luck.

If not, or you deleted the source (build) dir. than you'll just have to remove the files manually.

To what extent and where they were installed depends on the app which **you haven't mentioned.**


By default most sources will install to /usr/local unless you configured in a --prefix=/usr, then they'd be in /usr

The possible dir.'s files and or a folder would be in are (in either /usr/local or /usr 
bin
include
lib
share

You may or may not have a config file and or folder in your home dir.

---

### Post by hero1900 on 2009-06-12
thanks for help  it work i didn't delete the source folders
;)

---

