---
title: "I should know this, but I don't... how to upgrade GnuCash?"
date: 2009-01-09
forum: General Help
---

### Post by MountainX on 2009-01-09
I'm running Hardy. I installed GnuCash from the repository and it is v 2.2.4. I have not started using GnuCash yet, but I would like to get started with the latest version, which is 2.2.8. 

How do I upgrade? Synaptic is not reporting a newer version. I can download a deb file. Do I then need to uninstall my current version? Is there a command I can run that will upgrade using the deb file I download?

---

### Post by taurus on 2009-01-09
You can remove the old version from synaptic or from a terminal.  Then, you can install the new version either double-click it or from a terminal.

```
cd ~/Desktop
sudo dpk -i filename.deb
```

---

### Post by MountainX on 2009-01-09
First of all, am I correct to assume that version 2.2.8 will not be available in the Hardy repository? How is that determined?

Is there an easy way to specify that Synaptic look at the Intrepid repository for gnucash? How would I do that?

So far, I am not getting this installed. I uninstalled gnucash, gnucash-common and gnucash-docs. Then I just double-clicked the .deb file.

Error: Dependency is not satisfiable: gnucash-common.

I tried reinstalling the original version of gnucash-common. And this time I installed from a terminal. No success:

~$ sudo dpkg -i /home/myuser/Desktop/gnucash_2.2.8-1~getdeb1_i386.deb 
Selecting previously deselected package gnucash.
(Reading database ... 156880 files and directories currently installed.)
Unpacking gnucash (from .../gnucash_2.2.8-1~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on gnucash-common (>= 2.2.8-1~getdeb1); however:
  Version of gnucash-common on system is 2.2.4-1ubuntu1.
 gnucash depends on libgsf-1-114 (>= 1.14.8); however:
  Version of libgsf-1-114 on system is 1.14.7-2ubuntu1.
 gnucash depends on libgtk2.0-0 (>= 2.14.1); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
 gnucash depends on libpango1.0-0 (>= 1.21.6); however:
  Version of libpango1.0-0 on system is 1.20.5-0ubuntu1.
 gnucash depends on libpopt0 (>= 1.14); however:
  Version of libpopt0 on system is 1.10-3build1.
 gnucash depends on libxcb-render-util0; however:
  Package libxcb-render-util0 is not installed.
 gnucash depends on libxcb-render0; however:
  Package libxcb-render0 is not installed.
dpkg: error processing gnucash (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnucash

---

### Post by MountainX on 2009-01-09
I found v2.2.8 of gnucash-common and installed it first. However, now I get other dependency issues. I'm not sure if these can be easily resolved on Hardy. Any advice? Thanks.

dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on libgsf-1-114 (>= 1.14.8); however:
  Version of libgsf-1-114 on system is 1.14.7-2ubuntu1.
 gnucash depends on libgtk2.0-0 (>= 2.14.1); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
 gnucash depends on libpango1.0-0 (>= 1.21.6); however:
  Version of libpango1.0-0 on system is 1.20.5-0ubuntu1.
 gnucash depends on libpopt0 (>= 1.14); however:
  Version of libpopt0 on system is 1.10-3build1.
 gnucash depends on libxcb-render-util0; however:
  Package libxcb-render-util0 is not installed.
 gnucash depends on libxcb-render0; however:
  Package libxcb-render0 is not installed.
dpkg: error processing gnucash (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnucash

---

### Post by MountainX on 2009-01-09
solved

0. removed gnucash and gnucash-common (using Synaptic)
1. [http://www.getdeb.net/search.php?keywords=gnucash](http://www.getdeb.net/search.php?keywords=gnucash)
2. set version to hardy
3. download packages gnucash and gnucash-common
4. sudo dpkg -i /home/myuser/Desktop/gnucash-common_2.2.8-1~getdeb1_all.deb 
5. sudo dpkg -i /home/myuser/Desktop/gnucash_2.2.8-1~getdeb1_i386.deb 
6. I had to reinstall gnucash-docs because I removed it in step 0.

I would still like to know:
1. Will gnucash version 2.2.8 or above be available in the Hardy repository?
2. Once I have data in gnucash, how would I upgrade in order to keep my data? Same way? That doesn't feel very safe....

---

