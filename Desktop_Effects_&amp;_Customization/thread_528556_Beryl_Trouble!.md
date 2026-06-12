---
title: "Beryl Trouble!"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by s_spiff on 2007-08-18
I've used beryl beryl before, with no issues, and back then I had painstakingly installed using svn and other .debs. Now I used the universe repo for Feisty and I'm unable to get Beryl working. Somewhere down the line when I'm trying to start beryl-manager in the terminal, I get an error ( highlighter ), can someone help me out with this? 
This is the log in the Terminal right from the start where I sudo-apt the dependenice and core :
```
spiff@spiffed:~$ glxinfo | grep direct
direct rendering: Yes
spiff@spiffed:~$ sudo apt-get install beryl beryl-manager emerald-themes 
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
spiff@spiffed:~$ sudo apt-get install beryl beryl-manager emerald-themes 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  beryl-core beryl-plugins beryl-plugins-data beryl-settings
  beryl-settings-bindings emerald libberyldecoration0 libberylsettings0
  libemeraldengine0
Suggested packages:
  libberylsettings0-gconf libberylsettings0-kconfig
The following NEW packages will be installed:
  beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data
  beryl-settings beryl-settings-bindings emerald emerald-themes
  libberyldecoration0 libberylsettings0 libemeraldengine0
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 5124kB of archives.
After unpacking 14.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com feisty/universe libberylsettings0 0.2.1.dfsg+git20070318-0ubuntu2 [38.2kB]
Get:2 http://archive.ubuntu.com feisty/universe beryl-core 0.2.1.dfsg+git20070318-0ubuntu2 [177kB]
Get:3 http://archive.ubuntu.com feisty/universe beryl-plugins-data 0.2.1-0ubuntu2 [2354kB]
Get:4 http://archive.ubuntu.com feisty/universe libberyldecoration0 0.2.1.dfsg+git20070318-0ubuntu2 [16.9kB]
Get:5 http://archive.ubuntu.com feisty/universe beryl-plugins 0.2.1-0ubuntu2 [401kB]
Get:6 http://archive.ubuntu.com feisty/universe beryl-settings-bindings 0.2.1-0ubuntu1 [161kB]
Get:7 http://archive.ubuntu.com feisty/universe beryl-settings 0.2.1-0ubuntu1 [318kB]
Get:8 http://archive.ubuntu.com feisty/universe libemeraldengine0 0.2.1-0ubuntu1 [84.4kB]
Get:9 http://archive.ubuntu.com feisty/universe emerald 0.2.1-0ubuntu1 [212kB]
Get:10 http://archive.ubuntu.com feisty/universe beryl 0.2.1.dfsg+git20070318-0ubuntu2 [2758B]
Get:11 http://archive.ubuntu.com feisty/universe beryl-manager 0.2.1-0ubuntu1 [66.4kB]
Get:12 http://archive.ubuntu.com feisty/universe emerald-themes 0.2.1-0ubuntu1 [1290kB]
Fetched 5124kB in 32m8s (2657B/s)                                             
Selecting previously deselected package libberylsettings0.
(Reading database ... 129782 files and directories currently installed.)
Unpacking libberylsettings0 (from .../libberylsettings0_0.2.1.dfsg+git20070318-0ubuntu2_amd64.deb) ...
Selecting previously deselected package beryl-core.
Unpacking beryl-core (from .../beryl-core_0.2.1.dfsg+git20070318-0ubuntu2_amd64.deb) ...
Selecting previously deselected package beryl-plugins-data.
Unpacking beryl-plugins-data (from .../beryl-plugins-data_0.2.1-0ubuntu2_all.deb) ...
Selecting previously deselected package libberyldecoration0.
Unpacking libberyldecoration0 (from .../libberyldecoration0_0.2.1.dfsg+git20070318-0ubuntu2_amd64.deb) ...
Selecting previously deselected package beryl-plugins.
Unpacking beryl-plugins (from .../beryl-plugins_0.2.1-0ubuntu2_amd64.deb) ...
Selecting previously deselected package beryl-settings-bindings.
Unpacking beryl-settings-bindings (from .../beryl-settings-bindings_0.2.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package beryl-settings.
Unpacking beryl-settings (from .../beryl-settings_0.2.1-0ubuntu1_all.deb) ...
Selecting previously deselected package libemeraldengine0.
Unpacking libemeraldengine0 (from .../libemeraldengine0_0.2.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package emerald.
Unpacking emerald (from .../emerald_0.2.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package beryl.
Unpacking beryl (from .../beryl_0.2.1.dfsg+git20070318-0ubuntu2_amd64.deb) ...
Selecting previously deselected package beryl-manager.
Unpacking beryl-manager (from .../beryl-manager_0.2.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package emerald-themes.
Unpacking emerald-themes (from .../emerald-themes_0.2.1-0ubuntu1_all.deb) ...
Setting up libberylsettings0 (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up beryl-core (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up beryl-plugins-data (0.2.1-0ubuntu2) ...
Setting up libberyldecoration0 (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up beryl-plugins (0.2.1-0ubuntu2) ...
Setting up beryl-settings-bindings (0.2.1-0ubuntu1) ...

Setting up beryl-settings (0.2.1-0ubuntu1) ...
Setting up libemeraldengine0 (0.2.1-0ubuntu1) ...

Setting up emerald (0.2.1-0ubuntu1) ...

Setting up beryl (0.2.1.dfsg+git20070318-0ubuntu2) ...
Setting up beryl-manager (0.2.1-0ubuntu1) ...
Setting up emerald-themes (0.2.1-0ubuntu1) ...
spiff@spiffed:~$ beryl-manager
spiff@spiffed:~$ [COLOR=Red]**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
4241091 screens detected.[/COLOR]
Currently we cannot guarantee that Beryl will work correctly with multiple X screens.
Using the --no-context-share command line option can help.
Please report any success to the beryl developer mailing list. The list can be found at lists.beryl-project.org
Reloading...
Reloading...
Engine settings loaded

```

---

