---
title: "Compiz Fusion Group &amp; Tab Windows Missing!"
date: 2009-06-06
forum: Desktop Environments
---

### Post by Toadinator on 2009-06-06
For some odd reason, ever since I upgraded to ubuntu 9.04 I've been missing this pugin. I even checked in synaptic for the installed files for the extra plugins package, and the nessessary files aren't there! Why not? It was there before, correct? I have every single plugin except for this one and it was one of my favorites... Anyone else with the same problem, or did I do something wrong? I already tried re-installing the packages for the record...

---

### Post by clegends on 2009-06-07
me too, I miss this. Where is it?

---

### Post by Toadinator on 2009-06-19
bump... anyone got an idea what the problem is?

---

### Post by anechoic on 2009-06-22
bump - I have been missing this plugin as well on 9.04
:(

---

### Post by Toadinator on 2009-07-22
bump... anyone know the problem?

---

### Post by qpa_z_wonsem on 2009-08-02
same problem here
CompizConfig Settings Manager 0.8.2, same version for other packages.
Group and Tab and other new plugins not in ccsm.

any ideas?

oh! couldn't find any groupandtab.xml in usr/share/compiz

Thanks in advance

---

### Post by beterhans on 2009-08-12
dump I have the same problem
Linux Galaxy 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

---

### Post by Nate8nate on 2009-08-14
I just made it with git.

Here's how


Open Terminal and enter
```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```
```
mkdir ~/compizplugins
```
```
cd ~/compizplugins
```
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/group
```
```
cd group
```
```
make
```
```
BUILD_GLOBAL=true sudo make install
```
Restart Compiz or log out. 
It should show up in CCSM.

---

### Post by SoftwareExplorer on 2009-08-14
That's very odd, I have the plugin and I didn't have to build anything from source.
Do you have compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-plugins installed? I don't even have compiz-fusion-plugins-unsupported installed and I have the plugin.

From the files the various packages install, it looks like its the compiz-fusion-plugins-extra package that has it, but I'm not 100% sure on that.

---

### Post by Nate8nate on 2009-08-15
My animations addons plugin was missing too, and building it was the only way I could get it.  Others seem to have this problem, too.

---

