---
title: "Problems after installing and uninstalling kubuntu-desktop"
date: 2010-09-01
forum: Desktop Environments
---

### Post by amime on 2010-09-01
hi everybody ! 

under gnome  (OS: ubuntu lucid 10.04) i installed KGet and it was working fine with no problems or ( extra PKGs installation )  ... 
then  
i wanted to try KDE desktop so i installed kubuntu-desktop   , after that gnome windows and message alerts have been transformed to KDE form even if i was logged with gnome ... 

i uninstalled kubuntu-desktop using instructions provided here  :
[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

but then i lost kget  .... now   when i try to install it again , synaptic iforms me that i have to install a lot of extra packages as well .. 

what is the shortest way to install and run KDE program on my gnome desktop properly .. ?

thanks

---

### Post by utnubuuser on 2010-09-01
1.) In a terminal:> sudo dpkg-reconfigure gdm
2.) In a terminal:> sudo apt-get install nameofkdeapplication

Gnome and KDE apps (for most part) can be used in either environment.
Kubuntu vs. Ubuntu means different window managers - kdm/gdm
Running dpkg-reconfigure gdm allows you to choose which window manager is to be used...

---

### Post by amime on 2010-09-01
```

sudo dpkg-reconfigure gdm 
sudo apt-get install kget 
 
```
output : 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer libakonadiprivate1
  libattica0 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2
  libexiv2-6 libiodbc2 libmodplug0c2 libpackagekit-glib2-12
  libpackagekit-qt-12 libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant
  libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-test libsoprano4
  libssh-4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  oxygen-icon-theme packagekit packagekit-backend-apt phonon
  phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1 python-kde4
  python-packagekit python-qt4 python-sip shared-desktop-ontologies
  software-properties-kde soprano-daemon ttf-dejavu ttf-dejavu-extra
  update-manager-kde virtuoso-nepomuk
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin hspell
  khelpcenter akonadi-server libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 gxine xine-ui libxine1-doc
  libxine-doc libxine1-ffmpeg phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer kcm-phonon-xine python-qt4-dbg
The following NEW packages will be installed:
  exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kget kpackagekit kubuntu-debug-installer
  libakonadiprivate1 libattica0 libboost-program-options1.40.0 libclucene0ldbl
  libdbusmenu-qt2 libexiv2-6 libiodbc2 libmodplug0c2 libpackagekit-glib2-12
  libpackagekit-qt-12 libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant
  libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-test libsoprano4
  libssh-4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  oxygen-icon-theme packagekit packagekit-backend-apt phonon
  phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1 python-kde4
  python-packagekit python-qt4 python-sip shared-desktop-ontologies
  software-properties-kde soprano-daemon ttf-dejavu ttf-dejavu-extra
  update-manager-kde virtuoso-nepomuk
0 upgraded, 63 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.7MB/60.9MB of archives.
After this operation, 213MB of additional disk space will be used.
Do you want to continue [Y/n]? 


```

it says i have to download a lot of data and (213 MB ) of additional disk space will be used !!! 
why ..!

first time i downloaded nothing but KGet pkg .. 

thanks for responding quickly

---

### Post by karmila on 2010-09-01
> **amime said:**
> ```

sudo dpkg-reconfigure gdm 
sudo apt-get install kget 
 
```output : 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kpackagekit kubuntu-debug-installer libakonadiprivate1
  libattica0 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2
  libexiv2-6 libiodbc2 libmodplug0c2 libpackagekit-glib2-12
  libpackagekit-qt-12 libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant
  libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-test libsoprano4
  libssh-4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  oxygen-icon-theme packagekit packagekit-backend-apt phonon
  phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1 python-kde4
  python-packagekit python-qt4 python-sip shared-desktop-ontologies
  software-properties-kde soprano-daemon ttf-dejavu ttf-dejavu-extra
  update-manager-kde virtuoso-nepomuk
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin hspell
  khelpcenter akonadi-server libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 gxine xine-ui libxine1-doc
  libxine-doc libxine1-ffmpeg phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer kcm-phonon-xine python-qt4-dbg
The following NEW packages will be installed:
  exiv2 gdebi-kde icoutils install-package kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kdesudo kget kpackagekit kubuntu-debug-installer
  libakonadiprivate1 libattica0 libboost-program-options1.40.0 libclucene0ldbl
  libdbusmenu-qt2 libexiv2-6 libiodbc2 libmodplug0c2 libpackagekit-glib2-12
  libpackagekit-qt-12 libplasma3 libpolkit-qt-1-0 libqca2 libqt4-assistant
  libqt4-opengl libqt4-qt3support libqt4-scripttools libqt4-test libsoprano4
  libssh-4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  oxygen-icon-theme packagekit packagekit-backend-apt phonon
  phonon-backend-xine plasma-scriptengine-javascript polkit-kde-1 python-kde4
  python-packagekit python-qt4 python-sip shared-desktop-ontologies
  software-properties-kde soprano-daemon ttf-dejavu ttf-dejavu-extra
  update-manager-kde virtuoso-nepomuk
0 upgraded, 63 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.7MB/60.9MB of archives.
After this operation, 213MB of additional disk space will be used.
Do you want to continue [Y/n]? 


```it says i have to download a lot of data and (213 MB ) of additional disk space will be used !!! 
why ..!

first time i downloaded nothing but KGet pkg .. 

thanks for responding quickly

No, it's not need to download 213 MB but 40.7 MB.

Isn't it a lot of similar applications that work natively in gnome?

---

### Post by amime on 2010-09-02
> **karmila said:**
> No, it's not need to download 213 MB but 40.7 MB.

Isn't it a lot of similar applications that work natively in gnome?

i know that it's 40.7 MB .

about "similar applications " : i've tried all gnome native apps like : gwget , wget , cURL , Axel ,Aria2 , (FatRat) ,  JDownloader , UGet  , Downloader for the x  and multiget 


gwget : crashes a lot , and even when i close its window , the background process is still  running and occupying network resources ... 
wget , curl , axel and aria2 : the problem is the GUI and poor interaction .

jdownloader is "heavy " 

and vice versa .. 

++++++++++++++++++

anyway , i've installed those pkgs and kget is running , 

my question was about the existence of one -or more - pkg which is responsible for running kde apps under gnome as if they were gnome-oriented 

( interfaces and the use of binaries)

---

