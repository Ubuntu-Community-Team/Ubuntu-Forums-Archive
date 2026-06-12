---
title: "MISSING compizconfig-settings-manager in 7.10"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by barney66 on 2007-11-07
Hello to all...

could someone offer any help on this problem of not having access to compizconfig-settings-manager in 7.10

A search of the Synaptic Package Manager reveals the following packages are installed (green checkbox) -

compiz				1:0.6.0+git20071008-0ubuntu1.1
compiz-core			1:0.6.0+git20071008-0ubuntu1.1
compiz-fusion-plugins-extra 	0.5.2+git20070928-0ubuntu1
compiz-fusion-plugins-main 	0.5.2+git20070928-0ubuntu2
compiz-gnome		 	1:0.6.0+git20071008-0ubuntu1.1
compiz-plugins			1:0.6.0+git20071008-0ubuntu1.1
compiz-bcop			ARE NOT INSTALLED
compiz-dev			ARE NOT INSTALLED

I checked in a terminal by the following method

womble@womble-linux:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
You will have to enable component called 'universe'
bash: ccsm: command not found
womble@womble-linux:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for womble:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
womble@womble-linux:~$ 


I do have effects such as wobbly windows and I am using a restricted nVidia driver for a 6800GS card I just have no access to the config manager.... any help would be greatly appreciated.

regards,
barney66

---

### Post by avik on 2007-11-07
Go to System->Administration->System Sources, and enable universe.  Then try installing again.

---

### Post by barney66 on 2007-11-07
avik - thanks heaps, a simple fix and all is working fine... thanks thanks thanks ):P

---

