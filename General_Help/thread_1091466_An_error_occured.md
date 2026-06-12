---
title: "An error occured"
date: 2009-03-09
forum: General Help
---

### Post by tod1d on 2009-03-09
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help make that error message go away

---

### Post by kanikilu on 2009-03-09
Have you tried running ```
dpkg --configure -a
``` as it suggests?

---

### Post by tod1d on 2009-03-09
where would I type in that command?

I'm new to linux

---

### Post by kanikilu on 2009-03-09
Oh, ok, just do that in a terminal. Go to Applications > Accessories > Terminal to bring it up. Also, I think you'll want to add "sudo" to the beginning of that command: ```
sudo dpkg --configure -a
```

---

### Post by tod1d on 2009-03-09
> **kanikilu said:**
> Oh, ok, just do that in a terminal. Go to Applications > Accessories > Terminal to bring it up. Also, I think you'll want to add "sudo" to the beginning of that command: ```
sudo dpkg --configure -a
```

"brad@brad-desktop:~$" pops up next

---

### Post by tod1d on 2009-03-09
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 kdebase-runtime-data-common libxine1-misc-plugins libxcb-xv0 mysql-common kde-icons-oxygen libxine1-bin librasqal0
  libmysqlclient15off redland-utils kdelibs5-data libxcb-shape0 libstreamanalyzer0 libxvmc1 libpq5 libstreams0 libraptor1 libmodplug0c2 libaudio2
  libxcb-shm0 kdebase-runtime-data raptor-utils libmpcdec3 libxine1-console
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin sun-java6-jre unixodbc xutils-dev
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts libmyodbc odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 odbcinst1debian1 sun-java6-bin unixodbc xutils-dev
The following packages will be upgraded:
  sun-java6-jre
1 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/35.2MB of archives.
After this operation, 102MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

why did it abort?

---

### Post by tod1d on 2009-03-09
actualy this is working, my original error message went away and I was able to proceed on, 
thanks

---

