---
title: "Upgrading KDE 4.4.5 to 4.5.0"
date: 2010-08-10
forum: Desktop Environments
---

### Post by radko.dinev on 2010-08-10
Hello (good people)!

I am trying to upgrade KDE 4.4.5 to 4.5.0 (Kubuntu 10.04 LTS) but the attempt results in 22 packages that can be upgraded and 111 blocked updates.

The problem is due to a dependency issue with libqt4-assistant and ktorrent. aptutide offer me a solution to remove these two packages, as well as some other packages that seem important to me, and leave package kubuntu-desktop with unresolved dependencies. II don't know what that lib is needed for, but I use ktorrent every day. So this solution seems like a bad one to me.

Any ideas on how to upgrade to KDE 4.5 and keep ktorrent? 
Or is it better to wait for Kubuntu 10.10 release and then do a distro upgrade (which will surely get round the problem)?

Thanks in advance!

```
sharp@aparatus:~$ sudo aptitude full-upgrade
sudo: unable to resolve host aparatus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  ktorrent libqt4-assistant 
The following NEW packages will be installed:
  aurorae-themes-artwork{a} docbook-xml{a} docbook-xsl{a} docbook-xsl-doc-html{a} kdegraphics-libs-data{a} kdelibs5-plugins{a} kdepimlibs-kio-plugins{a} kdoctools{a} libakonadi-kabc4{a} libakonadi-kcal4{a} libakonadi-kde4{a} libakonadi-kmime4{a} libcln6{a} 
  libgpgme++2{a} libgps19{a} libkabc4{a} libkatepartinterfaces4{a} libkblog4{a} libkcal4{a} libkde3support4{a} libkdecore5{a} libkdesu5{a} libkdeui5{a} libkdewebkit5{a} libkdnssd4{a} libkfile4{a} libkholidays4{a} libkhtml5{a} libkimap4{a} libkimproxy4{a} libkio5{a} 
  libkjsapi4{a} libkjsembed4{a} libkldap4{a} libkmediaplayer4{a} libkmime4{a} libknewstuff2-4{a} libknewstuff3-4{a} libknotifyconfig4{a} libkntlm4{a} libkonqsidebarplugin4a{a} libkparts4{a} libkpimidentities4{a} libkpimtextedit4{a} libkpimutils4{a} libkpty4{a} 
  libkresources4{a} libkrosscore4{a} libkrossui4{a} libktexteditor4{a} libktnef4{a} libkunitconversion4{a} libkutils4{a} libkwineffects1a{a} libkxmlrpcclient4{a} libmailtransport4{a} libmicroblog4{a} libnepomuk4{a} libnepomukquery4a{a} libplasmaclock4b{a} 
  libprocesscore4a{a} libprocessui4a{a} libqalculate4{a} libqgpgme1{a} libqtwebkit4{a} libreadline5{a} libsolid4{a} libsolidcontrol4a{a} libsyndication4{a} libtaskmanager4a{a} libtelepathy-qt4-0{a} libthreadweaver4{a} libvirtodbc0{a} libweather-ion4a{a} sgml-data{a} 
  virtuoso-minimal{a} virtuoso-opensource-6.0-bin{a} virtuoso-opensource-6.0-common{a} 
The following packages will be REMOVED:
  freespacenotifier{a} kde-icons-nuvola{u} kdebase-plasma{a} kdepimlibs-data{a} libkfontinst4{a} libkonqsidebarplugin4{a} libkwineffects1{a} libplasma-applet-system-monitor4{a} libplasmaclock4{a} libprocesscore4{a} libprocessui4{a} libsolidcontrol4{a} 
  libtaskmanager4{a} libweather-ion4{a} 
The following packages will be upgraded:
  akonadi-server amarok amarok-common amarok-utils ark dolphin dragonplayer gwenview kamera kate kcalc kde-window-manager kde-zeroconf kdeartwork kdeartwork-emoticons kdeartwork-style kdeartwork-theme-icon kdebase-bin kdebase-data kdebase-runtime 
  kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepimlibs5 kdewallpapers kdm kfind kgpg 
  khelpcenter4 kinfocenter klipper kmag kmix kmousetool knm-runtime konqueror konqueror-nsplugins konsole kopete kppp krdc krfb krosspython kscreensaver kscreensaver-xsavers ksnapshot ksysguard ksysguardd ksystemlog ktorrent-data kubuntu-default-settings 
  kwalletmanager libakonadiprivate1 libattica0 libdbusmenu-qt2 libkcddb4 libkdcraw8 libkdecorations4 libkephal4 libkexiv2-8 libkipi7 libkonq5 libkonq5-templates libkopete4 libkscreensaver5 libksgrd4 libksignalplotter4 libkworkspace4 libmsn0.3 libokularcore1 
  libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmagenericshell4 libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg 
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libsolidcontrolifaces4 libsoprano4 network-manager-kde nuvola-icon-theme okular okular-extra-backends oxygen-icon-theme oxygen-icon-theme-complete phonon phonon-backend-xine 
  plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-desktopthemes-artwork plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus 
  plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo python-kde4 python-qt4 python-qt4-dbus python-sip shared-desktop-ontologies soprano-daemon system-config-printer-kde systemsettings 
132 packages upgraded, 78 newly installed, 14 to remove and 0 not upgraded.
Need to get 233MB of archives. After unpacking 94.1MB will be used.
The following packages have unmet dependencies:
  libqt4-assistant: Depends: libqt4-network (= 4:4.6.3-0ubuntu1) but 4:4.7.0~beta2-0ubuntu3~lucid1~ppa4 is to be installed.
                    Depends: libqtcore4 (= 4:4.6.3-0ubuntu1) but 4:4.7.0~beta2-0ubuntu3~lucid1~ppa4 is to be installed.
  ktorrent: Depends: libktorrent1 (>= 1.0.1) which is a virtual package.
            Depends: libktorrent-l10n which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
ktorrent
libqt4-assistant

Leave the following dependencies unresolved:
kubuntu-desktop recommends freespacenotifier
kubuntu-desktop recommends ktorrent
Score is -212
```

---

### Post by PicardyBeet on 2010-08-10
Shouldn't be a problem for a dist-upgrade
kubuntu-desktop is a virtual package,  like a list of all the package of a standard kubuntu-desktop. Ktorrent is a standard composant of Kubuntu, but by any mean a required package.

What could be a little bit more blocking is the case of *-dev package, if you have installed them in order to compile some kde or qt dependant programs by hands. You'll have to remove those *-dev package (and maybe automoc, and qt-designer).

---

### Post by utkjamie on 2010-08-10
Looks like the update wiped out Ktorrent for me. Here's what I'm getting:

```

The following packages have unmet dependencies:
  ktorrent: Depends: libktorrent1 (>= 1.0.1) but it is not installable
            Depends: libktorrent-l10n but it is not installable

```

**UPDATE: **After some updates that came later in the day, I was able to reinstall Ktorrent without a problem.

---

### Post by tintix on 2010-08-10
Hi guys. Got a temporary solution. Just found kTorrent 4.0.2 packages in launchpad that are built against kde 4.5.

You have to install these at once:
[http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/pool/main/k/ktorrent/ktorrent-data_4.0.2-3~kde45_all.deb]("http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/pool/main/k/ktorrent/ktorrent-data_4.0.2-3~kde45_all.deb")
[http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/pool/main/k/ktorrent/ktorrent_4.0.2-3~kde45_i386.deb]("http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/pool/main/k/ktorrent/ktorrent_4.0.2-3~kde45_i386.deb")
[http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/pool/main/libk/libktorrent/libktorrent1_1.0.2-2~ppa1_i386.deb]("http://ppa.launchpad.net/nuovodna/nuovodna-stuff/ubuntu/pool/main/libk/libktorrent/libktorrent1_1.0.2-2~ppa1_i386.deb")

---

### Post by starbone2 on 2010-08-10
thank you i had the same problem

i had to enter the two commands only

sudo add-apt-repository ppa:nuovodna/nuovodna-stuff
sudo apt-get install ktorrent

---

### Post by james_xxx on 2010-08-10
I am getting error messages in upgrading from 4.4.5 to 4.5.

I have added the nuovodna-stuff ppa to take care of the ktorrent issue, but am still seeing:

```
~$sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdebase-workspace-bin but it is not going to be installed
                   Recommends: freespacenotifier but it is not going to be installed
E: Broken packages

```

Also seeing this:
```

~$sudo apt-get install kdebase-workspace-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-workspace-bin: Depends: kdebase-workspace-data (= 4:4.5.0b-0ubuntu1~lucid1~ppa1) but 4:4.5.0b-0ubuntu1~lucid1~ppa2 is to be installed
E: Broken packages

```
AT present, KDM starts up upon rebooting, but gives me no option to log-in to a KDE session.

I'm using LXDE at the moment.

Any suggestions?

---

### Post by amelyst on 2010-08-11
I too upgraded my 10.04 from 4.4.x to 4.5. I got the same complaints from aptitude described by james_xxx.

I did a dist-upgrade and I got a 4.5 installation, but hey what a mess !

It turned out that all the kdepim packages, most notably kmail is missing from the ppa-backports repository. Kmail was left in version 4.4.x but was unable to start due to missing libraries.

<rant>
It was a pain to revert back to 4.4.x. I am wondering why there is no mention of this in the official announcement on kubuntu.org. And it is no the 3rd time a kubuntu backport kde upgrade ruined my installation. This does not speak well of the care taken for these repositories.
</rant>

---

### Post by james_xxx on 2010-08-11
bump

---

### Post by bzzzwa on 2010-08-11
I was unable to find KDE option at session menu at login screen after upgrade to 4.5.0 too. 

After
```
~$sudo apt-get install kubuntu-desktop
```
package and dependencies installed without problems now. Thx.

---

### Post by PicardyBeet on 2010-08-11
> **amelyst said:**
> I too upgraded my 10.04 from 4.4.x to 4.5. I got the same complaints from aptitude described by james_xxx.

I did a dist-upgrade and I got a 4.5 installation, but hey what a mess !

It turned out that all the kdepim packages, most notably kmail is missing from the ppa-backports repository. Kmail was left in version 4.4.x but was unable to start due to missing libraries.

</rant>

I've got Kmail in  version 4.4.5 working, after removing it, and then reinstalling it with  kdepim, libakonadi-contact4 and  libkontactinterface4.

Not a very streamed process, but it works.

---

### Post by radko.dinev on 2010-08-13
I managed to successfully upgrade KDE 4.4.5 to 4.5.0 using [FONT=Courier New]apt-get -f dist-upgrade[/FONT] 3 times in a row. The process was interrupted twice due to problems with some packages like qt4-assistant and libqt4-help.

Issuing the following commands did the job for me:

[FONT=Courier New]sudo apt-get -f dist-upgrade[/FONT] *("155 upgraded, 86 newly installed, 14 to remove and 0 not upgraded" in my case; everything downloaded but while unpacking at some moment an error interrupted the process)*
[FONT=Courier New]sudo apt-get -f dist-upgrade[/FONT] *(the process continued and after a while another error ocurred)*
[FONT=Courier New]sudo apt-get -f dist-upgrade[/FONT] *(the process continued, asked about updating the file /etc/kde4/kdm/kdmrc in the middle, and then finished without errors)*
[FONT=Courier New]sudo reboot
[/FONT][FONT=Courier New]
[/FONT]Maybe this could also be useful to you: [https://bugs.launchpad.net/kubuntu-ppa/+bug/615902](https://bugs.launchpad.net/kubuntu-ppa/+bug/615902)

---

### Post by killermike on 2010-08-22
I'm having some performance problems with KWIN and I'd like to know how to back out of KDE 4.5 and revert back to 4.4. I've googled around but I can't find instructions on the net.

Any information appreciated. Thanks.

---

### Post by jasontiller on 2010-08-30
Yo, killermike,

> **killermike said:**
> I'm having some performance problems with KWIN and I'd like to know how to back out of KDE 4.5 and revert back to 4.4. I've googled around but I can't find instructions on the net.

Any information appreciated. Thanks.

I was able to downgrade/revert to KDE 4.4 after an apt-get dist-upgrade to KDE SC 4.5.  However, it was *very* manual - nothing automated.  I wrote a Python script to do this:

1.  Go through the backports PPA

/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_backports_ubuntu_dists_lucid_main_binary-amd64_Packages

    and extract all of the package names in there.

2.  Using dpkg in --simulate mode, try to remove *every* package in backports.  Most of them weren't installed during dist-upgrade and will error out, but you can get a list of the backports packages that were actually installed.

3.  Using the info in the backports PPA list file, find the 4.4 packages that were replaced.  Either the 4.5 package will replace the exact same package in 4.4, or there'll be a "Replaces:" clause in the backports list that you use to figure out what 4.4 packages were replaced.

4.  Now, using dpkg, remove all of the 4.5 packages.

5.  Remove the backports PPA from apt's list of source repositories: /etc/apt/source.list.

6.  Run 'apt-get update' to rebuild the repository cache *without* the 4.5 (backports) repo.  This will make the 4.4 packages again be the latest-greatest.

7.  Run 'apt-get install -f' to install all of the dependencies for the currently-installed packages.  Because I used dpkg  to remove the 4.5 packages, there are now a *bunch* of packages that depend on KDE 4.5 packages that aren't installed.  apt-get refuses to do any more work until you fix those dependencies.

8.  Now run 'apt-get install' on all of the packages you determined that you needed in step 3.

It took a few days to figure out the files and write the script, and then it took an hour or so to run, but I'm now running KDE 4.4.2 on Qt 4.6.2 again.  Whew!

---Jason

---

