---
title: "Compiz Fusion with Intel Core 2 64-bit?"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-27
I've been trying to install Compiz Fusion for the past hour and always hit a wall at this error: 

```
myself@computer:~$ sudo aptitude install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-extra"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-unofficial"
Couldn't find any package whose name or description matched "libcompizconfig-backend-gconf"
The following packages are BROKEN:
  compiz 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.1kB of archives. After unpacking 65.5kB will be used.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
compiz [1:0.3.6-1ubuntu13 (feisty)]

Score is -10040

Accept this solution? [Y/n/q/?]
```

After trying to find a solution in the Synaptic Package Manager, I get this:

> compiz:
 Depends: compiz-decorator  but it is not installable


I searched and found another thread that says these packages are not available for 64-bit systems. As a user of a 64-bit Intel processor (Core 2 Duo) am I out of luck?

---

### Post by Dark Star on 2007-08-27
The 32bit ver. should run in 64bit too.. :) Well it seems you had already installed Cf of another repo.. Try searching COmpiz in Synaptic and remove the checked 1 :) Then try installing happen woth me yesterday :)

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-27
Removed everything related to compiz using synaptic, and this error persists:

```
myself@computer:~$ sudo aptitude install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-extra"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-unofficial"
Couldn't find any package whose name or description matched "libcompizconfig-backend-gconf"
The following packages are BROKEN:
  compiz 
The following packages have been automatically kept back:
  gpgv libgpgme11 liblame0 libqt4-core libqt4-gui libqt4-qt3support 
  libqt4-sql libxvidcore4 
The following NEW packages will be automatically installed:
  compiz-core compiz-gtk compiz-plugins 
The following packages have been kept back:
  clamav clamav-base clamav-freshclam gnome-btdownload gnupg hal 
  hal-device-manager irssi lftp libclamav2 libhal-storage1 libhal1 
  msttcorefonts 
The following NEW packages will be installed:
  compiz-core compiz-gnome compiz-gtk compiz-plugins libdecoration0 
0 packages upgraded, 6 newly installed, 0 to remove and 21 not upgraded.
Need to get 72.6kB/617kB of archives. After unpacking 3478kB will be used.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
compiz [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?]
```

as well as this, when I try to install normal compiz through synaptic:

> compiz:
Depends: compiz-decorator  but it is not installable

---

### Post by ferruiz on 2007-09-02
if you change the repositori ?

[http://forum.compiz-fusion.org/showthread.php?t=1012](http://forum.compiz-fusion.org/showthread.php?t=1012)

---

### Post by michael37 on 2007-09-02
**IMPORTANT!!!  See my next post before following instructions in this one: **

Please follow the guide in the post: [http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

In short, you need to clean uninstall before a clean install.

I am running 64-bit Ubuntu on Intel Core 2 Duo and Compiz Fusion runs great.

---

### Post by michael37 on 2007-09-02
> **boiiinnnnnnnnnnnnnnnnggg said:**
> Removed everything related to compiz using synaptic, and this error persists:

```
myself@computer:~$ sudo aptitude install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-extra"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-unofficial"
Couldn't find any package whose name or description matched "libcompizconfig-backend-gconf"
The following packages are BROKEN:
  compiz 
The following packages have been automatically kept back:
  gpgv libgpgme11 liblame0 libqt4-core libqt4-gui libqt4-qt3support 
  libqt4-sql libxvidcore4 
The following NEW packages will be automatically installed:
  compiz-core compiz-gtk compiz-plugins 
The following packages have been kept back:
  clamav clamav-base clamav-freshclam gnome-btdownload gnupg hal 
  hal-device-manager irssi lftp libclamav2 libhal-storage1 libhal1 
  msttcorefonts 
The following NEW packages will be installed:
  compiz-core compiz-gnome compiz-gtk compiz-plugins libdecoration0 
0 packages upgraded, 6 newly installed, 0 to remove and 21 not upgraded.
Need to get 72.6kB/617kB of archives. After unpacking 3478kB will be used.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
compiz [Not Installed]

Score is -10001

Accept this solution? [Y/n/q/?]
```

as well as this, when I try to install normal compiz through synaptic:

Actually, BEFORE you run the script that I suggested in the previous post, you gotta fix your packages.  Also, do not kill synaptic or apt-get to prevent re-occurance of this situation.  Run
```

sudo apt-get check

```
and accept all repairs that apt-get asks you to perform.  

Keep running this command until it runs clean (just doesn't print anything).  Then, follow the script that I quoted.

---

