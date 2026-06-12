---
title: "tzdata error"
date: 2009-03-04
forum: General Help
---

### Post by jimcuk on 2009-03-04
Hi folks

on attempting to install the latest updates I am getting the following error
any ideas please

regards
Jim


E: /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb: unable to install new version of `./usr/share/zoneinfo/posix/Canada/East-Saskatchewan'

---

### Post by jimcuk on 2009-03-04
just tried the following

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall tzdata


jim@jim-desktop:~$ sudo dpkg-reconfigure tzdata
/usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed.
jim@jim-desktop:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release  
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release [51.2kB]      
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [83.0kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages [303kB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [3491B]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [23.4kB]  
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [1154B] 
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [29.3kB]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [5440B]  
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [6406B]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [1860B]
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages [8097B]
Get: 15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources [96.2kB]
Get: 16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources [2474B]
Get: 17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages [74.1kB]
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources [17.9kB]
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages [10.9kB]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]
Fetched 767kB in 2s (298kB/s)                        
Reading package lists... Done
jim@jim-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-nonfree kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data khelpcenter4 libcurl3 libcurl3-gnutls
  libnm-glib0 libnm-util0 libvlc2 libvlccore0 mozilla-plugin-vlc
  network-manager network-manager-gnome tzdata vlc vlc-data vlc-nox
  vlc-plugin-esd
24 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
jim@jim-desktop:~$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
jim@jim-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-nonfree kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs5 kdelibs5-data khelpcenter4 libcurl3 libcurl3-gnutls
  libnm-glib0 libnm-util0 libvlc2 libvlccore0 mozilla-plugin-vlc
  network-manager network-manager-gnome tzdata vlc vlc-data vlc-nox
  vlc-plugin-esd
24 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1122kB/41.9MB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libcurl3 7.18.2-1ubuntu4.3 [220kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libcurl3-gnutls 7.18.2-1ubuntu4.3 [213kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libnm-util0 0.7~~svn20081018t105859-0ubuntu1.8.10.2 [72.1kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libnm-glib0 0.7~~svn20081018t105859-0ubuntu1.8.10.2 [55.0kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main network-manager 0.7~~svn20081018t105859-0ubuntu1.8.10.2 [264kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main network-manager-gnome 0.7~~svn20081020t000444-0ubuntu1.8.10.2 [299kB]
Fetched 1122kB in 3s (308kB/s)                
Preconfiguring packages ...
(Reading database ... 163024 files and directories currently installed.)
Preparing to replace tzdata 2008h-2ubuntu1 (using .../tzdata_2009b-0ubuntu0.8.10_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb (--unpack):
 unable to install new version of `./usr/share/zoneinfo/posix/Canada/East-Saskatchewan': Is a directory
dpkg: error while cleaning up:
 unable to remove newly-installed version of `/usr/share/zoneinfo/posix/Canada/East-Saskatchewan' to allow reinstallation of backup copy: Directory not empty
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-desktop:~$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
1 not fully installed or removed.
Need to get 0B/674kB of archives.
After this operation, 4096B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 163024 files and directories currently installed.)
Preparing to replace tzdata 2008h-2ubuntu1 (using .../tzdata_2009b-0ubuntu0.8.10_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb (--unpack):
 unable to install new version of `./usr/share/zoneinfo/posix/Canada/East-Saskatchewan': Is a directory
dpkg: error while cleaning up:
 unable to remove newly-installed version of `/usr/share/zoneinfo/posix/Canada/East-Saskatchewan' to allow reinstallation of backup copy: Directory not empty
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jimcuk on 2009-03-12
bumping this no ideas folks ?

---

### Post by jimcuk on 2009-03-14
Bit drastic I know but for future reference a format and re-install to solve this

regards
Jim

---

### Post by dcstar on 2009-03-15
> **jimcuk said:**
> 
..........
jim@jim-desktop:~$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  **tzdata**
1 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
1 not fully installed or removed.
Need to get 0B/674kB of archives.
After this operation, 4096B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 163024 files and directories currently installed.)
Preparing to replace tzdata 2008h-2ubuntu1 (using .../tzdata_2009b-0ubuntu0.8.10_all.deb) ...
Unpacking replacement tzdata ...
dpkg: error processing /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb (--unpack):
 unable to install new version of `./usr/share/zoneinfo/posix/Canada/East-Saskatchewan': Is a directory
dpkg: error while cleaning up:
 unable to remove newly-installed version of `/usr/share/zoneinfo/posix/Canada/East-Saskatchewan' to allow reinstallation of backup copy: Directory not empty
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2009b-0ubuntu0.8.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Do not "reinstall", in Synaptic firstly remove the package then clear the cache of downloaded packages.

Then just install the package.

---

### Post by jimcuk on 2009-03-15
thanks for response

synaptic would not let me de select the package

before I read your answer I had already reinstalled thanks anyway.

regards
JIm

---

