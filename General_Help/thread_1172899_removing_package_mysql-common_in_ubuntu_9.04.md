---
title: "removing package mysql-common in ubuntu 9.04"
date: 2009-05-29
forum: General Help
---

### Post by shin938 on 2009-05-29
Hi
i try to purge package mysql-common using synaptic or apt-get and it looks like its going to remove many unrelated packages,can someone explain that?
this is the output of apt-get purge

shin@shin-laptop:~$ sudo apt-get --simulate purge mysql-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqt4-opengl libxine1-x kdebase-runtime-data-common libwxgtk2.6-0 libqt4-dbus libxine1-misc-plugins
  libxcb-xv0 phonon libqt4-qt3support libapr1 kde-icons-oxygen libxine1-bin librasqal1 libqt4-webkit kdelibs5-data
  libqtcore4 libwxbase2.6-0 libxcb-shape0 libqt4-sql libqt4-svg phonon-backend-gstreamer libstreamanalyzer0 libphonon4
  libqt4-xml libqt4-network libqt4-designer libqtgui4 libpq5 libstreams0 libqt4-script libaudio2 libxcb-shm0
  kdebase-runtime-data qt4-qtconfig libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2* apache2-mpm-worker* apache2-utils* apache2.2-common* gstreamer0.10-plugins-bad* kate* kdebase-runtime*
  kdebase-runtime-bin-kde4* kdelibs-bin* kdelibs5* khelpcenter4* krusader* libapache2-svn* libaprutil1* libgmyth0*
  libmysqlclient15off* libplasma3* librdf0* libsoprano4* libsvn1* libsvncpp1* mysql-common* rapidsvn* redland-utils*
  soprano-daemon* subversion*
0 upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Purg apache2 [2.2.11-2ubuntu2]
Purg apache2-mpm-worker [2.2.11-2ubuntu2]
Purg libapache2-svn [1.5.4dfsg1-1ubuntu2]
Purg apache2.2-common [2.2.11-2ubuntu2]
Purg apache2-utils [2.2.11-2ubuntu2]
Purg gstreamer0.10-plugins-bad [0.10.11-2ubuntu1]
Purg kate [4:4.2.2-0ubuntu1]
Purg krusader [2.0.0-0ubuntu1]
Purg khelpcenter4 [4:4.2.2-0ubuntu1]
Purg kdebase-runtime [4:4.2.2-0ubuntu1] [kdebase-runtime-bin-kde4 ]
Purg kdebase-runtime-bin-kde4 [4:4.2.2-0ubuntu1]
Purg libplasma3 [4:4.2.2-0ubuntu5]
Purg kdelibs-bin [4:4.2.2-0ubuntu5] [kdelibs5 ]
Purg kdelibs5 [4:4.2.2-0ubuntu5]
Purg rapidsvn [0.9.6-1]
Purg libsvncpp1 [0.9.6-1]
Purg subversion [1.5.4dfsg1-1ubuntu2]
Purg libsvn1 [1.5.4dfsg1-1ubuntu2]
Purg libaprutil1 [1.2.12+dfsg-8]
Purg libgmyth0 [1:0.7.1-1ubuntu1]
Purg soprano-daemon [2.2.2+dfsg.1-1ubuntu1] [libsoprano4 ]
Purg libsoprano4 [2.2.2+dfsg.1-1ubuntu1]
Purg redland-utils [1.0.8-1]
Purg librdf0 [1.0.8-1]
Purg libmysqlclient15off [5.1.30really5.0.75-0ubuntu10]
Purg mysql-common [5.1.30really5.0.75-0ubuntu10]
shin@shin-laptop:~$

---

