---
title: "[SOLVED] cubeaddon"
date: 2008-07-05
forum: Desktop Environments
---

### Post by lenswipe on 2008-07-05
Ive seen loads of screenshots of the cubeaddon plugin for compiz and IMHO it looks wiked cool, but how do i install it on hardy heron?

I tried a command:

> git clone git://anongit.compiz-fusion.org/fusion/plugins/cubeaddon

but it didnt work.

Anyone have any ideas?

---

### Post by UbuntuNerd on 2008-07-05
found this somewhere

This guide is intended for use with Ubuntu Hardy Heron 8.04 compiz --version 0.7.*.
For those using Ubuntu 7.10 Gutsy Gibbon default compiz or compiz --version < 0.7.* this guide should not be used.
If you're not sure which version of compiz you have installed, you can use the command compiz --version to find out. If it returns 0.6.*, see the guide located here

This is not recommended to anyone not knowing exactly what they are doing.

For those who are using Ubuntu 8.04 Hardy Heron and would like to install additional plugins not provided in the hardy repositories, you've come to the right place. NOTE: Cubeaddon is a new plugin offering cube caps, cube deformation and reflection but will not work with Compiz 0.7.4; In order to get cubeaddon working, you will need to compile Compiz from source. Information on how to do this can be found here.

This tutorial assumes that:
1) You have a fresh install of Hardy.
2) You have Hardy's default compiz working (0.7.*).
3) You are running as user and not root.



Compiz-Fusion is installed by default in Ubuntu Hardy and will run as long as you have a video card with appropriate drivers installed and properly configured. Installing drivers is beyond the scope of this tutorial, but there are plenty of guides to configure your graphics card on Hardy; see the Hardware page on the Compiz Fusion Wiki for more information.

Getting the build dependencies
Install the packages required for compiling plugins:
Code:

sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

Getting the plugin source tarballs

Recommended: Create a subdirectory in which to store the code:
Code:

mkdir -p  ~/compiz/

In order to get the source, we'll use git. The syntax is 'git clone <URL>' where <URL> is the link specified in the summary of the plugin on gitweb. For sake of simplicity, I will provide commands to install some of the more popular plugins. To see what each plugin does, search YouTube.

Code:

cd ~/compiz
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/rcxdude/dialog
git clone git://anongit.compiz-fusion.org/users/warlock/freewins
git clone git://anongit.compiz-fusion.org/users/rcxdude/ghost
git clone git://anongit.compiz-fusion.org/users/b0le/photowheel
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
git clone git://anongit.compiz-fusion.org/fusion/plugins/tile
git clone git://anongit.compiz-fusion.org/fusion/plugins/wallpaper

The compiz API has changed. Use the following commands to download and unpack these plugins:

Code:

wget -O /tmp/snow.tar 'http://oreaus.googlepages.com/snow.tar'
wget -O /tmp/stars.tar 'http://oreaus.googlepages.com/stars.tar'
wget -O /tmp/fireflies.tar 'http://oreaus.googlepages.com/fireflies.tar'

tar -xf '/tmp/snow.tar' -C ~/compiz/
tar -xf '/tmp/stars.tar' -C ~/compiz/
tar -xf '/tmp/fireflies.tar' -C ~/compiz/


Compiling the plugins
Switch to the directory created after cloning from git.


Example: For Atlantis2, you would do this:
Code:

cd ~/compiz/atlantis2


Once you are in the directory, you can compile the plugin:

Code:

make
make install

After compiling
Restart compiz and ccsm.


Removing a plugin
If for any reason you want to uninstall a plugin, the following command can be used.
Code:

make uninstall

---

### Post by lenswipe on 2008-07-06
> **jperez78 said:**
> found this somewhere

This guide is intended for use with Ubuntu Hardy Heron 8.04 compiz --version 0.7.*.
For those using Ubuntu 7.10 Gutsy Gibbon default compiz or compiz --version < 0.7.* this guide should not be used.
If you're not sure which version of compiz you have installed, you can use the command compiz --version to find out. If it returns 0.6.*, see the guide located here

This is not recommended to anyone not knowing exactly what they are doing.

For those who are using Ubuntu 8.04 Hardy Heron and would like to install additional plugins not provided in the hardy repositories, you've come to the right place. NOTE: Cubeaddon is a new plugin offering cube caps, cube deformation and reflection but will not work with Compiz 0.7.4; In order to get cubeaddon working, you will need to compile Compiz from source. Information on how to do this can be found here.

This tutorial assumes that:
1) You have a fresh install of Hardy.
2) You have Hardy's default compiz working (0.7.*).
3) You are running as user and not root.



Compiz-Fusion is installed by default in Ubuntu Hardy and will run as long as you have a video card with appropriate drivers installed and properly configured. Installing drivers is beyond the scope of this tutorial, but there are plenty of guides to configure your graphics card on Hardy; see the Hardware page on the Compiz Fusion Wiki for more information.

Getting the build dependencies
Install the packages required for compiling plugins:
Code:

sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

Getting the plugin source tarballs

Recommended: Create a subdirectory in which to store the code:
Code:

mkdir -p  ~/compiz/

In order to get the source, we'll use git. The syntax is 'git clone <URL>' where <URL> is the link specified in the summary of the plugin on gitweb. For sake of simplicity, I will provide commands to install some of the more popular plugins. To see what each plugin does, search YouTube.

Code:

cd ~/compiz
git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
git clone git://anongit.compiz-fusion.org/users/rcxdude/dialog
git clone git://anongit.compiz-fusion.org/users/warlock/freewins
git clone git://anongit.compiz-fusion.org/users/rcxdude/ghost
git clone git://anongit.compiz-fusion.org/users/b0le/photowheel
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
git clone git://anongit.compiz-fusion.org/fusion/plugins/tile
git clone git://anongit.compiz-fusion.org/fusion/plugins/wallpaper

The compiz API has changed. Use the following commands to download and unpack these plugins:

Code:

wget -O /tmp/snow.tar 'http://oreaus.googlepages.com/snow.tar'
wget -O /tmp/stars.tar 'http://oreaus.googlepages.com/stars.tar'
wget -O /tmp/fireflies.tar 'http://oreaus.googlepages.com/fireflies.tar'

tar -xf '/tmp/snow.tar' -C ~/compiz/
tar -xf '/tmp/stars.tar' -C ~/compiz/
tar -xf '/tmp/fireflies.tar' -C ~/compiz/


Compiling the plugins
Switch to the directory created after cloning from git.


Example: For Atlantis2, you would do this:
Code:

cd ~/compiz/atlantis2


Once you are in the directory, you can compile the plugin:

Code:

make
make install

After compiling
Restart compiz and ccsm.


Removing a plugin
If for any reason you want to uninstall a plugin, the following command can be used.
Code:

make uninstall

ive done all that but still i cant get cubeaddon.. O_o

When i run those commands but with cube addon at the end i get this:
[http://pastebin.ubuntu.com/25416/](http://pastebin.ubuntu.com/25416/)

anyone have any ideas?


Well..


i run the commands and it makes the directory

so i navigate to the directory and then run make

and it does that. 

Anyone have any ideas?

---

### Post by sayakb on 2008-07-06
Upgrade to Compiz 0.7.6 which has this plugin installed by default. In System->Administration->Software Sources->Third Party Softwares, add this repo:
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

And reload the database. You will be notified of Compiz update. Do the update and reboot.

---

### Post by lenswipe on 2008-07-06
> **LinuxIsInnovation said:**
> Upgrade to Compiz 0.7.6 which has this plugin installed by default. In System->Administration->Software Sources->Third Party Softwares, add this repo:
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

And reload the database. You will be notified of Compiz update. Do the update and reboot.

I did it and it works, thx very much!

---

### Post by sayakb on 2008-07-06
Np.. Glad I could help!

---

### Post by skywalk on 2009-04-05
sayakb
many thanks
Now I can enjoy the cubeaddon effects.

---

