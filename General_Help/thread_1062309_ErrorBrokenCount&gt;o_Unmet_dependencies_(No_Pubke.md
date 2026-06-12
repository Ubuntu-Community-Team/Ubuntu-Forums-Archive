---
title: "Error:BrokenCount&gt;o Unmet dependencies (No Pubkey)"
date: 2009-02-06
forum: General Help
---

### Post by Morty007 on 2009-02-06
Hi all,

I've got a red minus sign that says " An error occurred, please run package manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was 'Error:BrokenCount>0' This usually means that your installed packages have unmet dependencies.


That's the whole error message. Here is what happens when I run apt-get update in terminal. 

marc@marc-laptop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/universe Packages
Fetched 198B in 0s (244B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
marc@marc-laptop:~$

---

### Post by DougieFresh4U on 2009-02-06
Have you tried:
```
sudo apt-get -f install
sudo dpkg--configure -a
```

That won't fix the key problem. You may want to go to Medibuntu site and get the key

---

### Post by Morty007 on 2009-02-06
Here's is what happens when i do that.

 sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gsfonts-x11 libavcodec51 odbcinst1debian1 sun-java6-bin sun-java6-jre
  unixodbc xutils-dev
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts libmyodbc
  odbc-postgresql libct1
The following NEW packages will be installed:
  gsfonts-x11 libavcodec51 odbcinst1debian1 sun-java6-bin unixodbc xutils-dev
The following packages will be upgraded:
  sun-java6-jre
1 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/38.7MB of archives.
After this operation, 111MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.


I'm not sure how to get the key like you said. I'm pretty new to Ubuntu.

---

### Post by zvacet on 2009-02-06
In terminal type
[B]
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -[/B]

---

### Post by Morty007 on 2009-02-06
zvacet- Thanks for replying. I fixed it somehow. I think I unabled it, and then re enabled it. Everything is fine now. Thanks though!:p

---

### Post by peyek on 2010-01-11
How about to handle this error?

sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-plasma python-dev libeet1 kdebase-bin libqzion0 python2.6-dev
  libqedje0 qt4-qtconfig
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-bin
Suggested packages:
  plasma-scriptengines
The following packages will be upgraded:
  kdebase-workspace-bin
1 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
Need to get 0B/3273kB of archives.
After this operation, 2970kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 202828 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.2.2-0ubuntu2 (using .../kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kconf_update_bin/plasma-add-shortcut-to-menu', which is also in package kde-window-manager
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

