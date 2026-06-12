---
title: "noob needs help with &quot;failed to fetch&quot; error"
date: 2009-06-03
forum: General Help
---

### Post by rap15 on 2009-06-03
Hello, I have no experience with Ubuntu, and I just installed ubuntu 9.04. I tried to download vlc media player as recommended and I get this error message in the synaptic package manager:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntu.com'


Can anybody please help? I'm sorry if I'm just dumb. Thank you.

---

### Post by michy99 on 2009-06-03
What is the output of```
cat /etc/apt/sources.list
```

---

### Post by rap15 on 2009-06-03
This is what I get:

ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by michy99 on 2009-06-03
What happens when you enter```
sudo apt-get update
```Note: You cannot run this while Synaptic Package Manager is open.

---

### Post by rap15 on 2009-06-03
This is what I get:

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg [189B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release [74.6kB]                        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release [49.6kB]               
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]                
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages [1253kB]                  
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages [8848B]             
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages [4757kB]              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages [197kB]            
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources [555kB]                   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources [3156B]             
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources [2375kB]              
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources [107kB]             
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages [24.9kB]        
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages [14B]     
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages [9226B]     
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages [14B]     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources [7756B]          
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources [14B]      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources [1941B]      
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources [14B]      
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [65.1kB]         
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [14B]      
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages [19.9kB]     
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages [675B]     
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [21.5kB]          
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [14B]       
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources [5564B]       
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources [639B]      
Fetched 9587kB in 2min 34s (62.0kB/s)                                          
Reading package lists... Done

---

### Post by michy99 on 2009-06-03
Try installing vlc from the terminal.```
sudo apt-get install vlc
```

---

### Post by rap15 on 2009-06-03
Well, this is what I got:

ubuntu@ubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libass1 libaudio2 libavcodec52 libavformat52 libavutil49
  libdca0 libdvbpsi4 libdvdnav4 libdvdread4 libebml0 libenca0 libfaad0
  libid3tag0 libiso9660-5 liblua5.1-0 libmad0 libmatroska0 libmodplug0c2
  libmpcdec3 libmpeg2-4 libmysqlclient15off libpostproc51 libqt4-dbus
  libqt4-designer libqt4-network libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libsdl-image1.2 libswscale0
  libtar libtwolame0 libvcdinfo0 libvlc2 libvlccore0 libx264-65 mysql-common
  qt4-qtconfig vlc-data vlc-nox
Suggested packages:
  nas libdvdcss2 debhelper fakeroot build-essential libqt4-dev
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  liba52-0.7.4 libass1 libaudio2 libavcodec52 libavformat52 libavutil49
  libdca0 libdvbpsi4 libdvdnav4 libdvdread4 libebml0 libenca0 libfaad0
  libid3tag0 libiso9660-5 liblua5.1-0 libmad0 libmatroska0 libmodplug0c2
  libmpcdec3 libmpeg2-4 libmysqlclient15off libpostproc51 libqt4-dbus
  libqt4-designer libqt4-network libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libsdl-image1.2 libswscale0
  libtar libtwolame0 libvcdinfo0 libvlc2 libvlccore0 libx264-65 mysql-common
  qt4-qtconfig vlc vlc-data vlc-nox
0 upgraded, 46 newly installed, 0 to remove and 104 not upgraded.
Need to get 28.8MB of archives.
After this operation, 83.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqtcore4 4.5.0-0ubuntu4.1 [1495kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-xml 4.5.0-0ubuntu4.1 [85.8kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-dbus 4.5.0-0ubuntu4.1 [176kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-script 4.5.0-0ubuntu4.1 [345kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libaudio2 1.9.1-5 [80.4kB]         
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqtgui4 4.5.0-0ubuntu4.1 [3638kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-designer 4.5.0-0ubuntu4.1 [1819kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-network 4.5.0-0ubuntu4.1 [387kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-sql 4.5.0-0ubuntu4.1 [85.5kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-qt3support 4.5.0-0ubuntu4.1 [1047kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main mysql-common 5.1.30really5.0.75-0ubuntu10.2 [62.9kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libmysqlclient15off 5.1.30really5.0.75-0ubuntu10.2 [1842kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libqt4-sql-mysql 4.5.0-0ubuntu4.1 [23.5kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main qt4-qtconfig 4.5.0-0ubuntu4.1 [81.1kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe liba52-0.7.4 0.7.4-11ubuntu1 [27.2kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libavutil49 3:0.svn20090303-1ubuntu6 [89.7kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libavcodec52 3:0.svn20090303-1ubuntu6 [3865kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libavformat52 3:0.svn20090303-1ubuntu6 [707kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libdvbpsi4 0.1.5-3.1 [32.6kB] 
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libdvdread4 4.1.3-4ubuntu2 [61.8kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libdvdnav4 4.1.3-3 [74.9kB]   
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libebml0 0.7.7-3.1 [63.7kB]   
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libenca0 1.9-6 [72.7kB]       
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libfaad0 2.6.1-3.1 [167kB]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libid3tag0 0.15.1b-10 [36.9kB]    
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libiso9660-5 0.78.2+dfsg1-3 [112kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main liblua5.1-0 5.1.4-2 [82.0kB]      
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libmad0 0.15.1b-4 [74.5kB]        
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libmatroska0 0.8.1-1.1 [196kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main libmodplug0c2 1:0.8.4-3ubuntu1.1 [172kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libmpcdec3 1.2.2-1build1 [27.4kB] 
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libmpeg2-4 0.4.1-3 [55.9kB]   
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libpostproc51 3:0.svn20090303-1ubuntu6 [67.7kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libsdl-image1.2 1.2.6-3 [30.1kB]  
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main libswscale0 3:0.svn20090303-1ubuntu6 [171kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libtar 1.2.11-5ubuntu1 [20.4kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libtwolame0 0.3.12-1 [53.6kB] 
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libvcdinfo0 0.7.23-4ubuntu1 [129kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse vlc-data 0.9.9a-2ubuntu1 [5858kB]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse libvlccore0 0.9.9a-2ubuntu1 [393kB]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse libvlc2 0.9.9a-2ubuntu1 [46.5kB]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse libx264-65 1:0.svn20081230-0.0ubuntu1 [298kB]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libass1 0.9.5-2 [40.1kB]      
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libdca0 0.0.5-0.1 [115kB]     
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse vlc-nox 0.9.9a-2ubuntu1 [2769kB]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse vlc 0.9.9a-2ubuntu1 [1692kB]
Fetched 28.8MB in 6min 13s (77.1kB/s)                                          
Extracting templates from packages: 100%
Selecting previously deselected package libqtcore4.
(Reading database ... 105940 files and directories currently installed.)
Unpacking libqtcore4 (from .../libqtcore4_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.1-5_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-designer.
Unpacking libqt4-designer (from .../libqt4-designer_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Selecting previously deselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package qt4-qtconfig.
Unpacking qt4-qtconfig (from .../qt4-qtconfig_4.5.0-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package liba52-0.7.4.
Unpacking liba52-0.7.4 (from .../liba52-0.7.4_0.7.4-11ubuntu1_i386.deb) ...
Selecting previously deselected package libavutil49.
Unpacking libavutil49 (from .../libavutil49_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libavcodec52.
Unpacking libavcodec52 (from .../libavcodec52_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libavformat52.
Unpacking libavformat52 (from .../libavformat52_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libdvbpsi4.
Unpacking libdvbpsi4 (from .../libdvbpsi4_0.1.5-3.1_i386.deb) ...
Selecting previously deselected package libdvdread4.
Unpacking libdvdread4 (from .../libdvdread4_4.1.3-4ubuntu2_i386.deb) ...
Selecting previously deselected package libdvdnav4.
Unpacking libdvdnav4 (from .../libdvdnav4_4.1.3-3_i386.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_i386.deb) ...
Selecting previously deselected package libenca0.
Unpacking libenca0 (from .../libenca0_1.9-6_i386.deb) ...
Selecting previously deselected package libfaad0.
Unpacking libfaad0 (from .../libfaad0_2.6.1-3.1_i386.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-10_i386.deb) ...
Selecting previously deselected package libiso9660-5.
Unpacking libiso9660-5 (from .../libiso9660-5_0.78.2+dfsg1-3_i386.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-2_i386.deb) ...
Selecting previously deselected package libmad0.
Unpacking libmad0 (from .../libmad0_0.15.1b-4_i386.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1.1_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.8.4-3ubuntu1.1_i386.deb) ...
Selecting previously deselected package libmpcdec3.
Unpacking libmpcdec3 (from .../libmpcdec3_1.2.2-1build1_i386.deb) ...
Selecting previously deselected package libmpeg2-4.
Unpacking libmpeg2-4 (from .../libmpeg2-4_0.4.1-3_i386.deb) ...
Selecting previously deselected package libpostproc51.
Unpacking libpostproc51 (from .../libpostproc51_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.6-3_i386.deb) ...
Selecting previously deselected package libswscale0.
Unpacking libswscale0 (from .../libswscale0_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-5ubuntu1_i386.deb) ...
Selecting previously deselected package libtwolame0.
Unpacking libtwolame0 (from .../libtwolame0_0.3.12-1_i386.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-4ubuntu1_i386.deb) ...
Selecting previously deselected package vlc-data.
Unpacking vlc-data (from .../vlc-data_0.9.9a-2ubuntu1_all.deb) ...
Selecting previously deselected package libvlccore0.
Unpacking libvlccore0 (from .../libvlccore0_0.9.9a-2ubuntu1_i386.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_0.9.9a-2ubuntu1_i386.deb) ...
Selecting previously deselected package libx264-65.
Unpacking libx264-65 (from .../libx264-65_1%3a0.svn20081230-0.0ubuntu1_i386.deb) ...
Selecting previously deselected package libass1.
Unpacking libass1 (from .../libass1_0.9.5-2_i386.deb) ...
Selecting previously deselected package libdca0.
Unpacking libdca0 (from .../libdca0_0.0.5-0.1_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_0.9.9a-2ubuntu1_i386.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_0.9.9a-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libqtcore4 (4.5.0-0ubuntu4.1) ...

Setting up libqt4-xml (4.5.0-0ubuntu4.1) ...

Setting up libqt4-dbus (4.5.0-0ubuntu4.1) ...

Setting up libqt4-script (4.5.0-0ubuntu4.1) ...

Setting up libaudio2 (1.9.1-5) ...

Setting up libqtgui4 (4.5.0-0ubuntu4.1) ...

Setting up libqt4-designer (4.5.0-0ubuntu4.1) ...

Setting up libqt4-network (4.5.0-0ubuntu4.1) ...

Setting up libqt4-sql (4.5.0-0ubuntu4.1) ...

Setting up libqt4-qt3support (4.5.0-0ubuntu4.1) ...

Setting up mysql-common (5.1.30really5.0.75-0ubuntu10.2) ...
Setting up libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2) ...

Setting up libqt4-sql-mysql (4.5.0-0ubuntu4.1) ...
Setting up qt4-qtconfig (4.5.0-0ubuntu4.1) ...

Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...

Setting up libavutil49 (3:0.svn20090303-1ubuntu6) ...

Setting up libavcodec52 (3:0.svn20090303-1ubuntu6) ...

Setting up libavformat52 (3:0.svn20090303-1ubuntu6) ...

Setting up libdvbpsi4 (0.1.5-3.1) ...

Setting up libdvdread4 (4.1.3-4ubuntu2) ...

Setting up libdvdnav4 (4.1.3-3) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up libenca0 (1.9-6) ...

Setting up libfaad0 (2.6.1-3.1) ...

Setting up libid3tag0 (0.15.1b-10) ...

Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up liblua5.1-0 (5.1.4-2) ...

Setting up libmad0 (0.15.1b-4) ...

Setting up libmatroska0 (0.8.1-1.1) ...

Setting up libmodplug0c2 (1:0.8.4-3ubuntu1.1) ...

Setting up libmpcdec3 (1.2.2-1build1) ...

Setting up libmpeg2-4 (0.4.1-3) ...

Setting up libpostproc51 (3:0.svn20090303-1ubuntu6) ...

Setting up libsdl-image1.2 (1.2.6-3) ...

Setting up libswscale0 (3:0.svn20090303-1ubuntu6) ...

Setting up libtar (1.2.11-5ubuntu1) ...

Setting up libtwolame0 (0.3.12-1) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vlc-data (0.9.9a-2ubuntu1) ...
Setting up libvlccore0 (0.9.9a-2ubuntu1) ...

Setting up libvlc2 (0.9.9a-2ubuntu1) ...

Setting up libx264-65 (1:0.svn20081230-0.0ubuntu1) ...

Setting up libass1 (0.9.5-2) ...

Setting up libdca0 (0.0.5-0.1) ...

Setting up vlc-nox (0.9.9a-2ubuntu1) ...
Setting up vlc (0.9.9a-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by michy99 on 2009-06-03
Looks like it installed. I suspect your problem before was caused by a temporary problem with your internet connection.

---

### Post by rap15 on 2009-06-03
Yes, I've tried it out and it seems like vlc is working. Thank you very much!!!! I don't know if it was a problem with my connection as I've tried it a number of times throughout the day, and I've been able to do other things online.

---

### Post by rap15 on 2009-06-03
I restarted the computer and it was deleted. I tried the synaptic package manager and it still showed the same error messages. Then, I tried the code and it installed again. Anyone know what I could be doing wrong?

---

### Post by michy99 on 2009-06-03
Are you running Ubuntu from a Live CD, or have you actually installed it on your hard drive?

---

### Post by rap15 on 2009-06-03
cd right now, is that the problem?

---

### Post by michy99 on 2009-06-03
Yes, any changes you make while running a Live CD go away when you shut down. To install anything permanently, you will have to install Ubuntu to your computer.

---

### Post by rap15 on 2009-06-03
Thanks. That makes sense.

---

### Post by rap15 on 2009-06-03
Thank you for your help!

---

