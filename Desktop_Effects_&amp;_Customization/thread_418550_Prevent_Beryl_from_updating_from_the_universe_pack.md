---
title: "Prevent Beryl from updating from the universe packages in Feisty - fglrx"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by mia1dolfan on 2007-04-22
This is mainly for users of GLX / FGLRX, for which the Beryl in the Feisty universe repository is broken.  For myself, the symptoms are white areas around the window border where the shadows should be, also at times the top and/or bottom of the cube are solid white, and also the cube background at times goes to a solid white.  When it goes white, it stays white, until logging out / in again.

The version of Beryl in the universe and the Beryl project are the same version.  I believe the packager for the Beryl packages in the universe repository changed the version so that it always supersedes the versions from official Beryl repository.

If you are affected, change your Beryl version back to the official ones built by the Beryl project, if you haven't done so already.

```
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-core_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-manager_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins-data_0.2.0~0beryl1_all.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins-unsupported_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-plugins-unsupported-data_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-settings_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-settings-bindings_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/emerald_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/emerald-themes_0.2.0~0beryl1_all.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/libberyldecoration0_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/libberylsettings0_0.2.0~0beryl1_i386.deb
wget http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/libemeraldengine0_0.2.0~0beryl1_i386.deb
sudo dkpg -i *beryl*.deb

```
For a full list of packages visit [http://ubuntu.beryl-project.org/pool/feisty/main](http://ubuntu.beryl-project.org/pool/feisty/main) *(Aquamarine, Heliodor, amd64, etc)*.  A alternative method for installing the Beryl packages include adding Beryl repository to apt-get list, disabling the universe repository, updating the package list, uninstalling and reinstalling the Beryl components, and finally re-enabling the universe repository.

Next time you run your favorite package manager *(Synaptic / Adept / apt-get, etc)* it's going to want to upgrade again because the packages in the universe have a newer version number.

Place the packages on hold so that they won't be auto selected for upgrade, customize to your liking.

```
sudo -v
echo beryl hold | sudo dpkg --set-selections
echo beryl-core hold | sudo dpkg --set-selections
echo beryl-manager hold | sudo dpkg --set-selections
echo beryl-plugins hold | sudo dpkg --set-selections
echo beryl-plugins-data hold | sudo dpkg --set-selections
echo beryl-plugins-unsupported hold | sudo dpkg --set-selections
echo beryl-plugins-unsupported-data hold | sudo dpkg --set-selections
echo beryl-settings hold | sudo dpkg --set-selections
echo beryl-settings-bindings hold | sudo dpkg --set-selections
echo emerald hold | sudo dpkg --set-selections
echo emerald-themes hold | sudo dpkg --set-selections
echo libberyldecoration0 hold | sudo dpkg --set-selections
echo libberylsettings0 hold | sudo dpkg --set-selections
echo libemeraldengine0 hold  | sudo dpkg --set-selections
```

Now the packages should show up as upgradeable in the packet manager, but not be auto selected for upgrade, unless you manually select them.  The affected Beryl version in the universe repository is 0.2.1.dfsg+git20070318-0ubuntu2.  Now you can keep a eye on it to see when it gets updated, at that point you can manually select the packages for upgrade, if the issue persists, re-install the Beryl packages from the Beryl repository.

To take the packages of hold status repeat the commands above replacing hold with install.  Please note even if you manually select the packages for upgrade, they will still remain with a hold status in the future.
```
sudo -v
echo beryl install | sudo dpkg --set-selections
echo beryl-core install | sudo dpkg --set-selections
echo beryl-manager install | sudo dpkg --set-selections
echo beryl-plugins install | sudo dpkg --set-selections
echo beryl-plugins-data install | sudo dpkg --set-selections
echo beryl-plugins-unsupported install | sudo dpkg --set-selections
echo beryl-plugins-unsupported-data install | sudo dpkg --set-selections
echo beryl-settings install | sudo dpkg --set-selections
echo beryl-settings-bindings install | sudo dpkg --set-selections
echo emerald install | sudo dpkg --set-selections
echo emerald-themes install | sudo dpkg --set-selections
echo libberyldecoration0 install | sudo dpkg --set-selections
echo libberylsettings0 install | sudo dpkg --set-selections
echo libemeraldengine0 install  | sudo dpkg --set-selections

```

---

### Post by Rinzwind on 2007-04-22
Thank You
Thank You
Thank You
Thank You
Oh and  Thank You.

edit: see [http://ubuntuforums.org/showthread.php?t=418431](http://ubuntuforums.org/showthread.php?t=418431) why O+

edit2:
echo emerald-themes hold  | sudo dpkg --set-selections
echo beryl-manager hold | sudo dpkg --set-selections

I also added these 2 since they where still tagged when I updated my repositories,

---

### Post by peakpc on 2007-04-28
Ditto the Thanks, I hope that they can fix this soon... But I here that beryl and compiz have gotten back together so maybe will have something new to try before long:)

---

