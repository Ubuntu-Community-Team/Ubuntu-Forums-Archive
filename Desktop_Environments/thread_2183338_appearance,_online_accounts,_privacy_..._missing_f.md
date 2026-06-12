---
title: "appearance, online accounts, privacy ... missing from settings saucy 13.10"
date: 2013-10-24
forum: Desktop Environments
---

### Post by papampi2 on 2013-10-24
some how appearance, online accounts, privacy ... missing from settings 

here is screen shot of seetings :

[IMG]https://dl.dropboxusercontent.com/u/5465144/Screenshot%20from%202013-10-24%2020%3A52%3A03.png[/IMG]


there are available in launcher but when i click it gets me to settings 

any idea how to solve it ?

---

### Post by papampi on 2013-10-25
I tried  install --reinstall ubuntu-desktop and gnome-control-center 

but problem is not solved

---

### Post by papampi on 2013-10-25
UBUNTU:~$  gnome-control-center 
background        display           network           power             search            user-accounts
bluetooth         info              notifications     printers          sharing           --verbose
color             keyboard          online-accounts   privacy           sound             --version
datetime          mouse             --overview        region            universal-access  wacom
UBUNTU:~$ gnome-control-center background 

** (gnome-control-center:14667): WARNING **: Ignoring launcher gufw (missing desktop file)

** (gnome-control-center:14667): WARNING **: Could not find settings panel "background"


please ... any one ?

---

### Post by mc4man on 2013-10-25
If you are using an ubuntu session (unity) then make sure this is installed
gnome-control-center-unity

if using a gnome session then you should note that in orig. post

---

### Post by papampi on 2013-10-25
Thanks for your reply, I'm using unity session and gnome-control-center-unity is installed and latest 

~$ sudo apt-get install gnome-control-center-unity 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-control-center-unity is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

but :

~$ gnome-control-center-unity 
gnome-control-center-unity: command not found

---

### Post by mc4man on 2013-10-25
> **papampi said:**
> Thanks for your reply, I'm using unity session and gnome-control-center-unity is installed and latest 

~$ sudo apt-get install gnome-control-center-unity 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-control-center-unity is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

but :

~$ gnome-control-center-unity 
gnome-control-center-unity: command not found
There is no command associated with that package

If you create a new user & log in to that user does system settings look & contain what it should?
(it's not that you're just missing some items, the whole look of it is also wrong

Is ubuntu-desktop installed? (just a meta package
If not then what, if anything,  additional would installing it pull in

```
sudo apt-get -s install ubuntu desktop
```

And just for info
```
apt-cache policy gnome-control-center
```

---

### Post by papampi on 2013-10-26
Thanks a lot for all your helps ;-)

> **mc4man said:**
> There is no command associated with that package

I thought so.

> **mc4man said:**
> 
If you create a new user & log in to that user does system settings look & contain what it should?
(it's not that you're just missing some items, the whole look of it is also wrong

Not home now, will check as soon as I get home. 

> **mc4man said:**
> 
Is ubuntu-desktop installed? (just a meta package
If not then what, if anything,  additional would installing it pull in

```
sudo apt-get -s install ubuntu desktop
```


```
PAYAM-UBUNTU:~$ sudo apt-get -s install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> **mc4man said:**
> 
And just for info
```
apt-cache policy gnome-control-center
```

```
payam@PAYAM-UBUNTU:~$ apt-cache policy gnome-control-center
gnome-control-center:
  Installed: 1:3.8.5-0ubuntu1~saucy1
  Candidate: 1:3.8.5-0ubuntu1~saucy1
  Version table:
 *** 1:3.8.5-0ubuntu1~saucy1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu44 0
        500 http://ir.archive.ubuntu.com/ubuntu/ saucy/main i386 Packages

```

---

### Post by mc4man on 2013-10-26
Well you're using g-c-c from one of the gnome3 ppa's & clearly it's not working correctly, at least in an ubuntu session. (3.8.5-0ubuntu1~saucy1
Why are you using that ppa?

---

### Post by papampi on 2013-10-26
dont remember when and I why I added that, may be yppa changed some old ppa to this one

so I will remove that ppa  and reinstall gnome-control-center , see if it will be ok or not

---

### Post by papampi on 2013-10-26
weird ....

```
PAYAM-UBUNTU:~$ sudo apt-get install --reinstall gnome-control-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of gnome-control-center is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by papampi on 2013-10-26
and there is no gnome-control-center in synaptic
its gnome-control-center1

should I remove gnome-control-center1 and install gnome-control-center ?

---

### Post by papampi on 2013-10-26
when wanted to remove gnome-control-center1 from synaptic i get this :

```

activity-log-manager will be removed
activity-log-manager-control-center will be removed
deja-dup will be removed
deja-dup-backend-gvfs will be removed
deja-dup-backend-ubuntuone will be removed
gnome-control-center will be removed
gnome-control-center-datetime will be removed
gnome-control-center-signon will be removed
gnome-control-center-unity will be removed
indicator-bluetooth will be removed
libgnome-control-center1 will be removed
ubuntu-desktop will be removed
webaccounts-extension-common will be removed
xul-ext-webaccounts will be removed
content-hub (version 0.0+13.10.20131011-0ubuntu1) will be installed
gsettings-ubuntu-touch-schemas (version 0.0.1+13.10.20130730-0ubuntu2) will be installed
indicator-network (version 0.5.1+13.10.20131015.2-0ubuntu1) will be installed
libandroid-properties1 (version 0.1.0+git20130606+c5d897a-0ubuntu35) will be installed
libcontent-hub0 (version 0.0+13.10.20131011-0ubuntu1) will be installed
libdee-qt5-3 (version 3.3+13.10.20130924.2-0ubuntu1) will be installed
libgflags2 (version 2.0-1ubuntu1) will be installed
libgoogle-glog0 (version 0.3.3-1) will be installed
libgsettings-qt1 (version 0.0+13.10.20130902.1-0ubuntu1) will be installed
libhud2 (version 13.10.1+13.10.20131014-0ubuntu1) will be installed
libhybris-common1 (version 0.1.0+git20130606+c5d897a-0ubuntu35) will be installed
libmirclient3 (version 0.0.15+13.10.20131014-0ubuntu1) will be installed
libmirplatform (version 0.0.15+13.10.20131014-0ubuntu1) will be installed
libmirprotobuf0 (version 0.0.15+13.10.20131014-0ubuntu1) will be installed
libmirserver7 (version 0.0.15+13.10.20131014-0ubuntu1) will be installed
libofono-qt1 (version 1.5+git20120419+bcf0c04-0ubuntu1) will be installed
libqdjango-db0 (version 0.4.0-1ubuntu1) will be installed
libqmenumodel0 (version 0.2.7+13.10.20131016-0ubuntu1) will be installed
libqt5feedback5 (version 5.0~git20130529-0ubuntu1) will be installed
libqt5multimedia5 (version 5.0.2-4ubuntu3) will be installed
libqt5multimediaquick-p5 (version 5.0.2-4ubuntu3) will be installed
libqt5organizer5 (version 5.0~git20130828-0ubuntu3) will be installed
libqt5qml-graphicaleffects (version 5.0.2-2ubuntu3) will be installed
libqt5svg5 (version 5.0.2-3ubuntu1) will be installed
libqt5systeminfo5 (version 5.0~git20130712-0ubuntu3) will be installed
libqt5xmlpatterns5 (version 5.0.2-2) will be installed
libsystemsettings1 (version 0.1+13.10.20131015.2-0ubuntu1) will be installed
libthumbnailer0 (version 1.0+13.10.20131011-0ubuntu1) will be installed
libubuntu-application-api-mirserver1 (version 0.19+13.10.20131015.1-0ubuntu1) will be installed
libubuntu-location-service0 (version 0.0.2+13.10.20131016.1-0ubuntu1) will be installed
libubuntu-platform-hardware-api1 (version 0.19+13.10.20131015.1-0ubuntu1) will be installed
libubuntudownloadmanager1 (version 0.2+13.10.20131016.1-0ubuntu1) will be installed
libunity-action-qt1 (version 1.0.0+13.10.20130716-0ubuntu1) will be installed
libunity-mir1 (version 0.1+13.10.20131016.1-0ubuntu1) will be installed
libunwind8 (version 1.1-2ubuntu3) will be installed
libupstart-app-launch1 (version 0.2+13.10.20131014-0ubuntu1) will be installed
libusermetricsoutput1 (version 1.1.1+13.10.20131003-0ubuntu1) will be installed
python3-gnupg (version 0.3.5-2) will be installed
qmenumodel-qml (version 0.2.7+13.10.20131016-0ubuntu1) will be installed
qtdeclarative5-accounts-plugin (version 0.3+13.10.20131016.1-0ubuntu1) will be installed
qtdeclarative5-dee-plugin (version 3.3+13.10.20130924.2-0ubuntu1) will be installed
qtdeclarative5-folderlistmodel-plugin (version 5.0.2-6ubuntu4) will be installed
qtdeclarative5-gsettings1.0 (version 0.0+13.10.20130902.1-0ubuntu1) will be installed
qtdeclarative5-qtfeedback-plugin (version 5.0~git20130529-0ubuntu1) will be installed
qtdeclarative5-qtmultimedia-plugin (version 5.0.2-4ubuntu3) will be installed
qtdeclarative5-qtquick2-plugin (version 5.0.2-6ubuntu4) will be installed
qtdeclarative5-systeminfo-plugin (version 5.0~git20130712-0ubuntu3) will be installed
qtdeclarative5-ubuntu-content0.1 (version 0.0+13.10.20131011-0ubuntu1) will be installed
qtdeclarative5-ubuntu-ui-toolkit-plugin (version 0.1.46+13.10.20131011.2-0ubuntu1) will be installed
qtdeclarative5-unity-action-plugin (version 1.0.0+13.10.20130716-0ubuntu1) will be installed
qtdeclarative5-unity-notifications-plugin (version 0.1.1+13.10.20131016-0ubuntu1) will be installed
qtdeclarative5-window-plugin (version 5.0.2-6ubuntu4) will be installed
qtdeclarative5-xmllistmodel-plugin (version 5.0.2-6ubuntu4) will be installed
sqlite3 (version 3.7.17-1ubuntu1) will be installed
system-image-common (version 1.9.1-0ubuntu1) will be installed
system-image-dbus (version 1.9.1-0ubuntu1) will be installed
ubuntu-download-manager (version 0.2+13.10.20131016.1-0ubuntu1) will be installed
ubuntu-keyboard-data (version 0.99.trunk.phablet2+13.10.20131016.1-0ubuntu1) will be installed
ubuntu-mobile-icons (version 13.04+13.10.20131014-0ubuntu1) will be installed
ubuntu-touch-sounds (version 13.10.1) will be installed
ubuntu-ui-toolkit-theme (version 0.1.46+13.10.20131011.2-0ubuntu1) will be installed
unity8 (version 7.83+13.10.20131016.2-0ubuntu1) will be installed
unity8-fake-env (version 7.83+13.10.20131016.2-0ubuntu1) will be installed
unity8-private (version 7.83+13.10.20131016.2-0ubuntu1) will be installed
usermetricsservice (version 1.1.1+13.10.20131003-0ubuntu1) will be installed

```

and a cannot be authentacted warning :

[IMG]https://dl.dropboxusercontent.com/u/5465144/Screenshot%20from%202013-10-26%2018%3A33%3A23.png[/IMG]

---

### Post by mc4man on 2013-10-26
> **papampi said:**
> dont remember when and I why I added that, may be yppa changed some old ppa to this one

so I will remove that ppa  and reinstall gnome-control-center , see if it will be ok or not

It would be better if you didn't remove the ppa & used ppa-purge instead

Plus you have have all these unity8 & mir packages & deps of  that aren't useful in 13.10, that 's where many of the  other packages to be installed are coming from

If manually reverting thru synaptic then you must remove **all **the gnome-control-center source  packages from the ppa (3.8.5..), refresh sources after removal, then re-install g-c-c & anything else removed that's needed. I would not log out or restart till you've squared up.

---

### Post by bapoumba on 2013-10-26
Just to make sure, could you please post your sources.list and ppas ?
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

---

### Post by papampi on 2013-10-26
> **bapoumba said:**
> Just to make sure, could you please post your sources.list and ppas ?
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```


payam@PAYAM-UBUNTU:~$ cat /etc/apt/sources.list
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ir.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse

###### Ubuntu Update Repos
deb http://ir.archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse
deb http://ir.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse

###### Ubuntu Partner Repo
#deb http://archive.canonical.com/ubuntu saucy partner
#deb-src http://archive.canonical.com/ubuntu saucy partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu saucy main
# deb-src http://extras.ubuntu.com/ubuntu sauscy main

##############################################################
##################### UNOFFICIAL REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Google Chrome Browser - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -

#### JDownloader PPA - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main

#### LibreOffice PPA - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu saucy main

#### muCommander - http://www.mucommander.com/
## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add -
# deb http://apt.mucommander.com stable main non-free contrib

#### Oracle Java (JDK) Installer PPA - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/java/ubuntu saucy main

#### Ubuntu Tweak PPA - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu saucy main

#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib

#### WebUpd8 PPA - http://www.webupd8.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main


####### 3rd Party Source Repos


#### JDownloader PPA (Source) - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main

#### LibreOffice PPA (Source) - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu saucy main

#### Oracle Java (JDK) Installer PPA (Source) - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu saucy main

#### Ubuntu Tweak PPA (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu saucy main

#### WebUpd8 PPA (Source) - http://www.webupd8.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main



```



wow.... so many old and unusefull ppas there 

~$ ls -l /etc/apt/sources.list.d/
```

total 492
-rw-r--r-- 1 root root 132 Oct 24 20:31 alecive-antigone-precise.list
-rw-r--r-- 1 root root 132 Oct 18 17:56 alecive-antigone-precise.list.distUpgrade
-rw-r--r-- 1 root root 132 Oct 24 20:31 alecive-antigone-precise.list.save
-rw-r--r-- 1 root root 130 Oct 24 20:31 apt-fast-stable-precise.list
-rw-r--r-- 1 root root 130 Oct 18 17:56 apt-fast-stable-precise.list.distUpgrade
-rw-r--r-- 1 root root 130 Oct 24 20:31 apt-fast-stable-precise.list.save
-rw-r--r-- 1 root root  81 May 24  2012 atareao-nautilus-extensions-precise.list.save
-rw-r--r-- 1 root root 134 Oct 24 20:31 atareao-sunflower-raring.list
-rw-r--r-- 1 root root 136 Oct 18 17:56 atareao-sunflower-raring.list.distUpgrade
-rw-r--r-- 1 root root 134 Oct 24 20:31 atareao-sunflower-raring.list.save
-rw-r--r-- 1 root root  71 Oct 24 20:31 clipgrab-team-ppa-precise.list
-rw-r--r-- 1 root root 135 Oct 18 11:44 clipgrab-team-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  71 Oct 24 20:31 clipgrab-team-ppa-precise.list.save
-rw-r--r-- 1 root root  72 Oct 18 11:44 clipgrab-team-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root  71 Oct 19 20:45 clipgrab-team-ppa-raring.list.save
-rw-r--r-- 1 root root  49 Apr 28  2012 dropbox.list.distUpgrade
-rw-r--r-- 1 root root  84 May  2  2012 dropbox.list.save
-rw-r--r-- 1 root root 144 Apr 28  2012 ferramroberto-gnome3-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 109 May  2  2012 ferramroberto-gnome3-oneiric.list.save
-rw-r--r-- 1 root root 140 Apr 28  2012 ferramroberto-java-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 107 May  2  2012 ferramroberto-java-oneiric.list.save
-rw-r--r-- 1 root root 150 Oct 24 20:31 folke-schwinning-personal-precise.list
-rw-r--r-- 1 root root 150 Oct 18 17:56 folke-schwinning-personal-precise.list.distUpgrade
-rw-r--r-- 1 root root 150 Oct 24 20:31 folke-schwinning-personal-precise.list.save
-rw-r--r-- 1 root root 150 Oct 24 20:31 fossfreedom-packagefixes-saucy.list
-rw-r--r-- 1 root root 150 Oct 24 20:31 fossfreedom-packagefixes-saucy.list.save
-rw-r--r-- 1 root root 132 Oct 24 20:31 freefilesync-ffs-quantal.list
-rw-r--r-- 1 root root 132 Oct 18 17:56 freefilesync-ffs-quantal.list.distUpgrade
-rw-r--r-- 1 root root 132 Oct 24 20:31 freefilesync-ffs-quantal.list.save
-rw-r--r-- 1 root root 235 Oct 24 20:31 google-chrome.list
-rw-r--r-- 1 root root 178 Oct 18 11:44 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 235 Oct 24 20:31 google-chrome.list.save
-rw-r--r-- 1 root root  55 Oct 18 11:44 google.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 19 18:51 google.list.save
-rw-r--r-- 1 root root 152 Oct 24 20:31 hakermania-format-junkie-precise.list
-rw-r--r-- 1 root root 222 Oct 18 11:44 hakermania-format-junkie-precise.list.distUpgrade
-rw-r--r-- 1 root root 152 Oct 24 20:31 hakermania-format-junkie-precise.list.save
-rw-r--r-- 1 root root 154 Oct 24 20:31 hydr0g3n-qbittorrent-stable-raring.list
-rw-r--r-- 1 root root 156 Oct 18 17:57 hydr0g3n-qbittorrent-stable-raring.list.distUpgrade
-rw-r--r-- 1 root root 154 Oct 24 20:31 hydr0g3n-qbittorrent-stable-raring.list.save
-rw-r--r-- 1 root root 152 Oct 24 20:31 ikarosdev-unity-revamped-precise.list
-rw-r--r-- 1 root root 222 Oct 18 11:44 ikarosdev-unity-revamped-precise.list.distUpgrade
-rw-r--r-- 1 root root 152 Oct 24 20:31 ikarosdev-unity-revamped-precise.list.save
-rw-r--r-- 1 root root 138 Oct 19 19:09 jd-team-jdownloader-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 108 May  2  2012 jd-team-jdownloader-oneiric.list.save
-rw-r--r-- 1 root root 118 Oct 24 20:31 jfi-ppa-precise.list
-rw-r--r-- 1 root root 116 Oct 18 11:44 jfi-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 118 Oct 24 20:31 jfi-ppa-precise.list.save
-rw-r--r-- 1 root root   0 Sep 17 23:52 kokoto-java-omgubuntu-stuff-raring.list
-rw-r--r-- 1 root root   0 Sep 17 23:52 kokoto-java-omgubuntu-stuff-raring.list.save
-rw-r--r-- 1 root root 148 Apr 28  2012 merlwiz79-cinnamon-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 107 May  2  2012 merlwiz79-cinnamon-ppa-oneiric.list.save
-rw-r--r-- 1 root root 158 Oct 24 20:31 musicbrainz-developers-stable-precise.list
-rw-r--r-- 1 root root 158 Oct 18 17:57 musicbrainz-developers-stable-precise.list.distUpgrade
-rw-r--r-- 1 root root 158 Oct 24 20:31 musicbrainz-developers-stable-precise.list.save
-rw-r--r-- 1 root root  83 Feb  1  2012 nathan-renniewaldock-xbmc-nightly-oneiric.list.save
-rw-r--r-- 1 root root 140 Oct 19 19:09 nilarimogard-webupd8-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 109 May  2  2012 nilarimogard-webupd8-oneiric.list.save
-rw-r--r-- 1 root root 142 Oct 19 19:09 n-muench-programs-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 110 May  2  2012 n-muench-programs-ppa-oneiric.list.save
-rw-r--r-- 1 root root 124 Oct 19 19:09 n-muench-vlc-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 101 May  2  2012 n-muench-vlc-oneiric.list.save
-rw-r--r-- 1 root root 140 Oct 18 17:57 noobslab-indicators-raring.list.distUpgrade
-rw-r--r-- 1 root root 138 Oct 19 19:41 noobslab-indicators-raring.list.save
-rw-r--r-- 1 root root 144 Oct 24 20:31 noobslab-swar-themes-precise.list
-rw-r--r-- 1 root root 214 Oct 18 11:44 noobslab-swar-themes-precise.list.distUpgrade
-rw-r--r-- 1 root root 144 Oct 24 20:31 noobslab-swar-themes-precise.list.save
-rw-r--r-- 1 root root  80 Oct 24 20:31 oneiric-partner.list
-rw-r--r-- 1 root root  80 Oct 18 17:57 oneiric-partner.list.distUpgrade
-rw-r--r-- 1 root root  80 Oct 24 20:31 oneiric-partner.list.save
-rw-r--r-- 1 root root  45 Oct 24 20:31 playonlinux.list
-rw-r--r-- 1 root root  47 Oct 18 11:44 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root  45 Oct 24 20:31 playonlinux.list.save
-rw-r--r-- 1 root root 157 Oct 24 20:31 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root 184 Oct 19 19:10 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade
-rw-r--r-- 1 root root 157 Oct 24 20:31 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root 126 Oct 24 20:31 relan-exfat-precise.list
-rw-r--r-- 1 root root 124 Oct 18 11:44 relan-exfat-precise.list.distUpgrade
-rw-r--r-- 1 root root 126 Oct 24 20:31 relan-exfat-precise.list.save
-rw-r--r-- 1 root root 112 Oct 24 20:31 steam.list
-rw-r--r-- 1 root root 112 Oct 19 19:12 steam.list.distUpgrade
-rw-r--r-- 1 root root 112 Oct 24 20:31 steam.list.save
-rw-r--r-- 1 root root  62 May  7  2012 suraia-ppa-precise.list.save
-rw-r--r-- 1 root root 128 Oct 24 20:31 team-xbmc-ppa-quantal.list
-rw-r--r-- 1 root root 128 Oct 18 11:44 team-xbmc-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root 128 Oct 24 20:31 team-xbmc-ppa-quantal.list.save
-rw-r--r-- 1 root root 201 Oct 24 20:31 team-xbmc-ppa-saucy.list
-rw-r--r-- 1 root root 201 Oct 24 20:31 team-xbmc-ppa-saucy.list.save
-rw-r--r-- 1 root root 144 Oct 24 20:31 thefanclub-grive-tools-raring.list
-rw-r--r-- 1 root root 146 Oct 18 17:58 thefanclub-grive-tools-raring.list.distUpgrade
-rw-r--r-- 1 root root 144 Oct 24 20:31 thefanclub-grive-tools-raring.list.save
-rw-r--r-- 1 root root  66 May  7  2012 tiheum-equinox-precise.list.save
-rw-r--r-- 1 root root 142 Oct 24 20:31 tldm217-tahutek_net-precise.list
-rw-r--r-- 1 root root 142 Oct 18 11:44 tldm217-tahutek_net-precise.list.distUpgrade
-rw-r--r-- 1 root root 142 Oct 24 20:31 tldm217-tahutek_net-precise.list.save
-rw-r--r-- 1 root root 130 Oct 24 20:31 tualatrix-ppa-precise.list
-rw-r--r-- 1 root root 126 Oct 18 17:58 tualatrix-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 130 Oct 24 20:31 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root  67 Oct 24 20:31 tualatrix-ppa-raring.list
-rw-r--r-- 1 root root  67 Oct 18 17:58 tualatrix-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root  67 Oct 24 20:31 tualatrix-ppa-raring.list.save
-rw-r--r-- 1 root root 148 Oct 19 19:10 ubuntu-mozilla-daily-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 109 May  2  2012 ubuntu-mozilla-daily-ppa-oneiric.list.save
-rw-r--r-- 1 root root 158 Oct 24 20:31 ubuntu-mozilla-security-ppa-oneiric.list
-rw-r--r-- 1 root root 158 Oct 18 11:44 ubuntu-mozilla-security-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 158 Oct 24 20:31 ubuntu-mozilla-security-ppa-oneiric.list.save
-rw-r--r-- 1 root root 130 Oct 24 20:31 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root 196 Oct 18 17:58 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 130 Oct 24 20:31 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root 154 Oct 24 20:31 unity-webapps-feedly-stable-raring.list
-rw-r--r-- 1 root root 156 Oct 18 17:58 unity-webapps-feedly-stable-raring.list.distUpgrade
-rw-r--r-- 1 root root 154 Oct 24 20:31 unity-webapps-feedly-stable-raring.list.save
-rw-r--r-- 1 root root   0 Sep  1 21:10 upubuntu-com-flareget-i386-raring.list.save
-rw-r--r-- 1 root root 134 Apr 29 21:17 webapps-preview-precise.list.distUpgrade
-rw-r--r-- 1 root root 134 Aug 11 18:23 webapps-preview-precise.list.save
-rw-r--r-- 1 root root 150 Oct 24 20:31 webupd8team-experiments-raring.list
-rw-r--r-- 1 root root 150 Oct 18 11:44 webupd8team-experiments-raring.list.distUpgrade
-rw-r--r-- 1 root root 150 Oct 24 20:31 webupd8team-experiments-raring.list.save
-rw-r--r-- 1 root root 142 Oct 24 20:31 webupd8team-puddletag-precise.list
-rw-r--r-- 1 root root 142 Oct 18 17:59 webupd8team-puddletag-precise.list.distUpgrade
-rw-r--r-- 1 root root 142 Oct 24 20:31 webupd8team-puddletag-precise.list.save
-rw-r--r-- 1 root root 150 Oct 24 20:31 webupd8team-y-ppa-manager-raring.list
-rw-r--r-- 1 root root 152 Oct 18 17:59 webupd8team-y-ppa-manager-raring.list.distUpgrade
-rw-r--r-- 1 root root 150 Oct 24 20:31 webupd8team-y-ppa-manager-raring.list.save
-rw-r--r-- 1 root root 160 Oct 24 20:31 werner-jaeger-ppa-werner-vpn-quantal.list
-rw-r--r-- 1 root root 158 Oct 18 13:28 werner-jaeger-ppa-werner-vpn-quantal.list.distUpgrade
-rw-r--r-- 1 root root 160 Oct 24 20:31 werner-jaeger-ppa-werner-vpn-quantal.list.save

```

---

### Post by papampi on 2013-10-26
mc4man ,..... 

you are the man ;)
its almost done appearance, brightness and lock, and online accounts are back after removed gnome ppa > removed g-c-c > update > install g-c-c

the only thing missing now is privacy and security and I cant find the package for that :(

---

### Post by bapoumba on 2013-10-26
I'm going to leave you with mc4man :)

Just to note :
```
# deb-src http://extras.ubuntu.com/ubuntu sauscy main
```
The repo is commented out, but there is a typo in "sauscy"

In addition, you have a sarge ppa, did not check what's in there, but that *could* explain your package manager being confused.

---

### Post by papampi on 2013-10-26
Thanks a lot bapoumba for your help 
so can I remove all the ppas that are not saucy ?
and also should I remove that sarge ppa?

---

### Post by mc4man on 2013-10-26
As far as  'security & privacy' panel - 
```
sudo apt-get install activity-log-manager
```

---

### Post by papampi on 2013-10-26
> **mc4man said:**
> As far as  'security & privacy' panel - 
```
sudo apt-get install activity-log-manager
```

Awesome man ....

thats fixed too

---

### Post by mc4man on 2013-10-26
Before removing ppa'a you may want to open synaptic > click on "Origin" tab & see what, if anything, you have installed from any of those ppa's

Then if packages are from this or that ppa,  determine if they're  needed or what may be the consequence of removing & proceed accordingly

---

### Post by papampi on 2013-10-26
Thanx a lot man ...
you guys been so very helpful ;)

---

### Post by bapoumba on 2013-10-26
> **mc4man said:**
> Before removing ppa'a you may want to open synaptic > click on "Origin" tab & see what, if anything, you have installed from any of those ppa's

Then if packages are from this or that ppa,  determine if they're  needed or what may be the consequence of removing & proceed accordingly
Thanks mc4man. The sarge ppa is for webmin, looks the sarge repo is their current : [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by mc4man on 2013-10-26
At some point you may want to check 'autoremove' to see what's avail. to remove.
 (can be done in synaptic though I'd suggest running a simulation thru apt-get first & reading carefully
```
sudo apt-get -s autoremove
```

You can also use an apt-get sim to ck. what removing a package(s) could produce, again careful read back is more important then just seeing  if the sim completes without error
sudo apt-get -s purge whatever

---

### Post by papampi on 2013-10-27
Thanks for all the helps,
Now I have a Duplicate source problem...
```

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) saucy/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_saucy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
but apt-get update wont solve it

cat /etc/apt/sources.list
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ir.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse

###### Ubuntu Update Repos
deb http://ir.archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse
deb http://ir.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu saucy partner
deb-src http://archive.canonical.com/ubuntu saucy partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main

##############################################################
##################### UNOFFICIAL REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Google Chrome Browser - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -

#### JDownloader PPA - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main

#### LibreOffice PPA - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444

#### Ubuntu Tweak PPA - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu saucy main

#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib

#### WebUpd8 PPA - http://www.webupd8.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main


####### 3rd Party Source Repos

#### JDownloader PPA (Source) - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu saucy main

#### Ubuntu Tweak PPA (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu saucy main

#### WebUpd8 PPA (Source) - http://www.webupd8.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4C9D234C
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu saucy main

```

ls -l /etc/apt/sources.list.d/
```


total 440
-rw-r--r-- 1 root root   0 Oct 26 23:26 alecive-antigone-precise.list
-rw-r--r-- 1 root root 132 Oct 18 17:56 alecive-antigone-precise.list.distUpgrade
-rw-r--r-- 1 root root  68 Oct 26 23:26 alecive-antigone-precise.list.save
-rw-r--r-- 1 root root 130 Oct 27 01:25 apt-fast-stable-precise.list
-rw-r--r-- 1 root root 130 Oct 18 17:56 apt-fast-stable-precise.list.distUpgrade
-rw-r--r-- 1 root root 130 Oct 27 01:25 apt-fast-stable-precise.list.save
-rw-r--r-- 1 root root  81 May 24  2012 atareao-nautilus-extensions-precise.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:15 atareao-sunflower-raring.list
-rw-r--r-- 1 root root 136 Oct 18 17:56 atareao-sunflower-raring.list.distUpgrade
-rw-r--r-- 1 root root  69 Oct 27 01:15 atareao-sunflower-raring.list.save
-rw-r--r-- 1 root root  71 Oct 27 01:25 clipgrab-team-ppa-precise.list
-rw-r--r-- 1 root root 135 Oct 18 11:44 clipgrab-team-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  71 Oct 27 01:25 clipgrab-team-ppa-precise.list.save
-rw-r--r-- 1 root root  72 Oct 18 11:44 clipgrab-team-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root  71 Oct 19 20:45 clipgrab-team-ppa-raring.list.save
-rw-r--r-- 1 root root  49 Apr 28  2012 dropbox.list.distUpgrade
-rw-r--r-- 1 root root  84 May  2  2012 dropbox.list.save
-rw-r--r-- 1 root root 144 Apr 28  2012 ferramroberto-gnome3-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 109 May  2  2012 ferramroberto-gnome3-oneiric.list.save
-rw-r--r-- 1 root root 140 Apr 28  2012 ferramroberto-java-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 107 May  2  2012 ferramroberto-java-oneiric.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:23 folke-schwinning-personal-precise.list
-rw-r--r-- 1 root root 150 Oct 18 17:56 folke-schwinning-personal-precise.list.distUpgrade
-rw-r--r-- 1 root root  77 Oct 27 01:23 folke-schwinning-personal-precise.list.save
-rw-r--r-- 1 root root 148 Oct 27 01:25 fossfreedom-packagefixes-saucy.list
-rw-r--r-- 1 root root 148 Oct 27 01:25 fossfreedom-packagefixes-saucy.list.save
-rw-r--r-- 1 root root 132 Oct 27 01:25 freefilesync-ffs-quantal.list
-rw-r--r-- 1 root root 132 Oct 18 17:56 freefilesync-ffs-quantal.list.distUpgrade
-rw-r--r-- 1 root root 132 Oct 27 01:25 freefilesync-ffs-quantal.list.save
-rw-r--r-- 1 root root 235 Oct 27 01:25 google-chrome.list
-rw-r--r-- 1 root root 178 Oct 18 11:44 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 235 Oct 27 01:25 google-chrome.list.save
-rw-r--r-- 1 root root  55 Oct 18 11:44 google.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 19 18:51 google.list.save
-rw-r--r-- 1 root root 152 Oct 27 01:25 hakermania-format-junkie-precise.list
-rw-r--r-- 1 root root 222 Oct 18 11:44 hakermania-format-junkie-precise.list.distUpgrade
-rw-r--r-- 1 root root 152 Oct 27 01:25 hakermania-format-junkie-precise.list.save
-rw-r--r-- 1 root root 154 Oct 27 01:25 hydr0g3n-qbittorrent-stable-raring.list
-rw-r--r-- 1 root root 156 Oct 18 17:57 hydr0g3n-qbittorrent-stable-raring.list.distUpgrade
-rw-r--r-- 1 root root 154 Oct 27 01:25 hydr0g3n-qbittorrent-stable-raring.list.save
-rw-r--r-- 1 root root 152 Oct 27 01:25 ikarosdev-unity-revamped-precise.list
-rw-r--r-- 1 root root 222 Oct 18 11:44 ikarosdev-unity-revamped-precise.list.distUpgrade
-rw-r--r-- 1 root root 152 Oct 27 01:25 ikarosdev-unity-revamped-precise.list.save
-rw-r--r-- 1 root root 138 Oct 19 19:09 jd-team-jdownloader-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 108 May  2  2012 jd-team-jdownloader-oneiric.list.save
-rw-r--r-- 1 root root 118 Oct 27 01:25 jfi-ppa-precise.list
-rw-r--r-- 1 root root 116 Oct 18 11:44 jfi-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 118 Oct 27 01:25 jfi-ppa-precise.list.save
-rw-r--r-- 1 root root   0 Sep 17 23:52 kokoto-java-omgubuntu-stuff-raring.list
-rw-r--r-- 1 root root   0 Sep 17 23:52 kokoto-java-omgubuntu-stuff-raring.list.save
-rw-r--r-- 1 root root 148 Apr 28  2012 merlwiz79-cinnamon-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 107 May  2  2012 merlwiz79-cinnamon-ppa-oneiric.list.save
-rw-r--r-- 1 root root 162 Oct 27 01:54 musicbrainz-developers-stable-precise.list
-rw-r--r-- 1 root root 158 Oct 18 17:57 musicbrainz-developers-stable-precise.list.distUpgrade
-rw-r--r-- 1 root root 158 Oct 27 01:25 musicbrainz-developers-stable-precise.list.save
-rw-r--r-- 1 root root  83 Feb  1  2012 nathan-renniewaldock-xbmc-nightly-oneiric.list.save
-rw-r--r-- 1 root root 140 Oct 19 19:09 nilarimogard-webupd8-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 109 May  2  2012 nilarimogard-webupd8-oneiric.list.save
-rw-r--r-- 1 root root 142 Oct 19 19:09 n-muench-programs-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 110 May  2  2012 n-muench-programs-ppa-oneiric.list.save
-rw-r--r-- 1 root root 124 Oct 19 19:09 n-muench-vlc-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 101 May  2  2012 n-muench-vlc-oneiric.list.save
-rw-r--r-- 1 root root 140 Oct 18 17:57 noobslab-indicators-raring.list.distUpgrade
-rw-r--r-- 1 root root 138 Oct 19 19:41 noobslab-indicators-raring.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:16 noobslab-swar-themes-precise.list
-rw-r--r-- 1 root root 214 Oct 18 11:44 noobslab-swar-themes-precise.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 27 01:16 noobslab-swar-themes-precise.list.save
-rw-r--r-- 1 root root  80 Oct 27 01:25 oneiric-partner.list
-rw-r--r-- 1 root root  80 Oct 18 17:57 oneiric-partner.list.distUpgrade
-rw-r--r-- 1 root root  80 Oct 27 01:25 oneiric-partner.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:16 playonlinux.list
-rw-r--r-- 1 root root  47 Oct 18 11:44 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 27 01:16 playonlinux.list.save
-rw-r--r-- 1 root root 157 Oct 27 01:25 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root 184 Oct 19 19:10 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade
-rw-r--r-- 1 root root 155 Oct 27 01:25 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:16 relan-exfat-precise.list
-rw-r--r-- 1 root root 124 Oct 18 11:44 relan-exfat-precise.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 27 01:16 relan-exfat-precise.list.save
-rw-r--r-- 1 root root 112 Oct 27 01:25 steam.list
-rw-r--r-- 1 root root 112 Oct 19 19:12 steam.list.distUpgrade
-rw-r--r-- 1 root root 112 Oct 27 01:25 steam.list.save
-rw-r--r-- 1 root root  62 May  7  2012 suraia-ppa-precise.list.save
-rw-r--r-- 1 root root 128 Oct 27 01:25 team-xbmc-ppa-quantal.list
-rw-r--r-- 1 root root 128 Oct 18 11:44 team-xbmc-ppa-quantal.list.distUpgrade
-rw-r--r-- 1 root root 128 Oct 27 01:25 team-xbmc-ppa-quantal.list.save
-rw-r--r-- 1 root root  67 Oct 27 01:25 team-xbmc-ppa-saucy.list
-rw-r--r-- 1 root root  67 Oct 27 01:25 team-xbmc-ppa-saucy.list.save
-rw-r--r-- 1 root root 144 Oct 27 01:25 thefanclub-grive-tools-raring.list
-rw-r--r-- 1 root root 146 Oct 18 17:58 thefanclub-grive-tools-raring.list.distUpgrade
-rw-r--r-- 1 root root 144 Oct 27 01:25 thefanclub-grive-tools-raring.list.save
-rw-r--r-- 1 root root  66 May  7  2012 tiheum-equinox-precise.list.save
-rw-r--r-- 1 root root 142 Oct 27 01:25 tldm217-tahutek_net-precise.list
-rw-r--r-- 1 root root 142 Oct 18 11:44 tldm217-tahutek_net-precise.list.distUpgrade
-rw-r--r-- 1 root root 142 Oct 27 01:25 tldm217-tahutek_net-precise.list.save
-rw-r--r-- 1 root root 130 Oct 27 01:25 tualatrix-ppa-precise.list
-rw-r--r-- 1 root root 126 Oct 18 17:58 tualatrix-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 130 Oct 27 01:25 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root  67 Oct 27 01:25 tualatrix-ppa-raring.list
-rw-r--r-- 1 root root  67 Oct 18 17:58 tualatrix-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root  67 Oct 27 01:25 tualatrix-ppa-raring.list.save
-rw-r--r-- 1 root root 148 Oct 19 19:10 ubuntu-mozilla-daily-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 109 May  2  2012 ubuntu-mozilla-daily-ppa-oneiric.list.save
-rw-r--r-- 1 root root 158 Oct 27 01:25 ubuntu-mozilla-security-ppa-oneiric.list
-rw-r--r-- 1 root root 158 Oct 18 11:44 ubuntu-mozilla-security-ppa-oneiric.list.distUpgrade
-rw-r--r-- 1 root root 158 Oct 27 01:25 ubuntu-mozilla-security-ppa-oneiric.list.save
-rw-r--r-- 1 root root 130 Oct 27 01:25 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root 196 Oct 18 17:58 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root 130 Oct 27 01:25 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root 154 Oct 27 01:25 unity-webapps-feedly-stable-raring.list
-rw-r--r-- 1 root root 156 Oct 18 17:58 unity-webapps-feedly-stable-raring.list.distUpgrade
-rw-r--r-- 1 root root 154 Oct 27 01:25 unity-webapps-feedly-stable-raring.list.save
-rw-r--r-- 1 root root   0 Sep  1 21:10 upubuntu-com-flareget-i386-raring.list.save
-rw-r--r-- 1 root root 134 Apr 29 21:17 webapps-preview-precise.list.distUpgrade
-rw-r--r-- 1 root root 134 Aug 11 18:23 webapps-preview-precise.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:16 webupd8team-experiments-raring.list
-rw-r--r-- 1 root root 150 Oct 18 11:44 webupd8team-experiments-raring.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 27 01:16 webupd8team-experiments-raring.list.save
-rw-r--r-- 1 root root 146 Oct 27 01:47 webupd8team-puddletag-precise.list
-rw-r--r-- 1 root root 142 Oct 18 17:59 webupd8team-puddletag-precise.list.distUpgrade
-rw-r--r-- 1 root root 142 Oct 27 01:25 webupd8team-puddletag-precise.list.save
-rw-r--r-- 1 root root 150 Oct 27 01:25 webupd8team-y-ppa-manager-raring.list
-rw-r--r-- 1 root root 152 Oct 18 17:59 webupd8team-y-ppa-manager-raring.list.distUpgrade
-rw-r--r-- 1 root root 150 Oct 27 01:25 webupd8team-y-ppa-manager-raring.list.save
-rw-r--r-- 1 root root   0 Oct 27 01:16 werner-jaeger-ppa-werner-vpn-quantal.list
-rw-r--r-- 1 root root 158 Oct 18 13:28 werner-jaeger-ppa-werner-vpn-quantal.list.distUpgrade
-rw-r--r-- 1 root root   0 Oct 27 01:16 werner-jaeger-ppa-werner-vpn-quantal.list.save

```

EDIT:

seems the oneiric-partner.list was made duplicate warning, removed it with 
```

sudo rm /etc/apt/sources.list.d/oneiric-partner.list*

```

and its fixed ;)

---

### Post by papampi on 2013-10-27
Another question,

There are plenty old ppa in /etc/apt/sources.list.d for raring, oneiric, ....
Do I need to change them to saucy ? 
if yes how ?

---

### Post by mc4man on 2013-10-27
> **papampi said:**
> Another question,

There are plenty old ppa in /etc/apt/sources.list.d for raring, oneiric, ....
Do I need to change them to saucy ? 
if yes how ?
There is no use changing any to saucy if the ppa doesn't have saucy builds, in that case you should remove them

Some once wrote a script that would check, don't remember where though (in one of the dev archives

Otherwise go to each ppa page & check

Ex. - this one does not have saucy builds (yet or maybe never?
[https://launchpad.net/~werner-jaeger/+archive/ppa-werner-vpn](https://launchpad.net/~werner-jaeger/+archive/ppa-werner-vpn)

I usually edit in "Software & Updates",  sometimes easier to edit a disabled ppa, the entry of concern is "Distribution"

---

