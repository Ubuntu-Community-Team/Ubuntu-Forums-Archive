---
title: "Help with apt-get"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by lagooned on 2007-11-07
Hello im running ubuntu 7.04 (upgraded from 6.10 if that helps at all)
i was looking on this forum like 15 min ago when i found a app 4 costimising compiz, i never had tried compiz so i installed the app it was: gnome-compiz-manager
so one i installed it i opened it up i found that compiz didnt work. i thought that this was due to my version of compiz so i installed compiz again.
i said 
$ sudo apt-get install compiz 
then it said something like:
The following packages will be upgraded:
  compiz-gnome
The following packages will be replaced:
 compiz-gtk
Are you sure you want to do this Y/n (or something like that): 

me being new to apt-get, i said yes

then when i it got done i tried to install another compiz costimation app. 
i got this: 

E: Sub-process /usr/bin/dpkg returned an error code (1)

i got worried and tried to reinstall compiz-gtk
 and when i did i got this:
sudo apt-get install -f compiz-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

i've tried everything, done exactly what is said:
sudo apt-get install -f compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java sdljump-data liquidwar-server libglitz-glx1 libcvsservice0
  lincity-ng-data libnl1-pre6 librdf0 network-manager libwww-ssl0 libkjsembed1
  libsdl-gfx1.2-4 trigger-data libnm-util0 libzvbi0 kdevelop-data libpcap0.7
  python-pyogg gftp-common libsqlite0 xmame-common libdv-bin snes9x-x
  gdk-imlib1 mencoder librasqal0 libseda-java libcommons-cli-java libgtk-jni
  libsnack2 python-pyvorbis kdesvn-kio-plugins libalut0 libcairo-java dhcdbd
  librpcsecgss2 python-mutagen cvs libbcprov-java libzvbi-common libxine-main1
  libglitz1 libglib-java neverdata kamefu-data python-wxversion libsvnqt3
  libkamefu0 libgtk-java python-wxgtk2.6 openvpn libzvt2 xmame-sdl
  liballegro4.2 tuxkart-data liquidwar-data
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 1376kB of additional disk space will be used.
(Reading database ... 163724 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

And then i tried:  sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java sdljump-data liquidwar-server libglitz-glx1 libcvsservice0
  lincity-ng-data libnl1-pre6 librdf0 network-manager libwww-ssl0 libkjsembed1
  libsdl-gfx1.2-4 trigger-data libnm-util0 libzvbi0 kdevelop-data libpcap0.7
  python-pyogg gftp-common libsqlite0 xmame-common libdv-bin snes9x-x
  gdk-imlib1 mencoder librasqal0 libseda-java libcommons-cli-java libgtk-jni
  libsnack2 python-pyvorbis kdesvn-kio-plugins libalut0 libcairo-java dhcdbd
  librpcsecgss2 python-mutagen cvs libbcprov-java libzvbi-common libxine-main1
  libglitz1 libglib-java neverdata kamefu-data python-wxversion libsvnqt3
  libkamefu0 libgtk-java python-wxgtk2.6 openvpn libzvt2 xmame-sdl
  liballegro4.2 tuxkart-data liquidwar-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 1376kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163724 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please if you can help me, Installing applications is pretty much all i like to do. And compiz is not that important to me, i just wanted to try it, thank you.

---

### Post by dianwen on 2007-11-09
Actually, if you are really willing to use Compiz Fusion, you can upgrade your distro to 7.10. CF is preinstalled in 7.10. Also, I believe if you install the dependencies mentioned, apt-get should be able to install Compiz. If not, you can Google this topic. It's very widely know.

---

