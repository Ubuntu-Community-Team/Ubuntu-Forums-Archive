---
title: "Dual Desktop - Kubuntu on Ubuntu"
date: 2009-02-19
forum: Desktop Environments
---

### Post by Mad_Max_1412 on 2009-02-19
Guys,

In APCMag in the March 2009 issue, there was an article on how Ubuntu users could try out the Kubuntu desktop.

It said all you need to do to install the Kubuntu desktop was to type the following command line:

sudo apt-get install kubuntu-desktop

When I do that, I get the following:

> max@ubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: phonon-backend-xine but it is not going to be installed
E: Broken packages

Does this need to be bought to someone's attention as it says a bug report should be filed?

I'm using Ubuntu 8.10

Thanks
Max

---

### Post by jonobe on 2009-02-19
I also found a similar thing - that I couldn't install kde/kubuntu through the repositories straight from Ubuntu.
Instead, I downloaded a Kubuntu live cd, and booted this up.  

A few tweaks later and my desktop is completely transformed.  KDE is a great modern (unlike gnome) looker, far superior to Windows.  You can't say gnome takes on windows in the looks department, can you?

I wonder why KDE is not the default for Ubuntu in fact.  Why not have it as the default, and have 'Gubuntu' for those who want a gnome version?  That's my two bits worth.

---

### Post by jacksaff on 2009-02-19
Run 'sudo apt-get update' and try again. Broken packages in the main repositories are rare and get fixed quickly. If it's still broken, post here again.

---

### Post by Lateralis on 2009-02-19
I've just tried to install kde-desktop, but that didn't work either.  

Given the original error message - posted above by another user - I tried the following:


install kubuntu-desktop phonon-backend-xine

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kubuntu-desktop: Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: dragonplayer but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
                   Depends: kde-zeroconf but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kuser but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: adept but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: gdebi-kde but it is not going to be installed
                   Recommends: guidance-power-manager but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kde-printer-applet but it is not going to be installed
                   Recommends: kdebase-plasma but it is not going to be installed
                   Recommends: kdebluetooth but it is not going to be installed
                   Recommends: kdepim-kresources but it is not going to be installed
                   Recommends: kdepim-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdeplasma-addons but it is not going to be installed
                   Recommends: kdesudo but it is not going to be installed
                   Recommends: kgrubeditor but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: konqueror-plugin-searchbar but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kopete but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: krdc but it is not going to be installed
                   Recommends: krfb but it is not going to be installed
                   Recommends: ktimetracker but it is not going to be installed
                   Recommends: ktorrent but it is not going to be installed
                   Recommends: kubuntu-docs but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: kvkbd but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: okular-extra-backends but it is not going to be installed
                   Recommends: plasmoid-quickaccess but it is not going to be installed
                   Recommends: update-notifier-kde but it is not going to be installed
E: Broken packages


I'm using Ubuntu 8.10.

---

### Post by HavocXphere on 2009-02-19
Not sure...the command seems to be the right one. Just checked on my kubuntu system and its definitely "kubuntu-desktop". Can't see the kde-desktop on my system.

I suspect that there is some clash between phonon (kde) and pulseaudio (gnome)...but thats just pure speculation.

---

### Post by shayguitarra on 2009-02-19
I posted this message ([http://ubuntuforums.org/showthread.php?t=1074635](http://ubuntuforums.org/showthread.php?t=1074635)) before I realised that the problem is similar to the one being discussed here.

As you can see I had already been running kubuntu and it's only since I installed the latest updates that it seems to have disappeared.

I tried to install through terminal, and ran sudo apt-get update but with no joy.

Any help?

---

### Post by krazyd on 2009-02-19
Try using 'aptitude' in place of 'apt-get'. It will offer different methods of resolving the problem.

---

### Post by shayguitarra on 2009-02-20
Ok, this is how I solved the problem:

I went here: [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

I followed the instructions for Intrepid and then ran software update.

Afterwards when I went to install kubuntu desktop through synaptic all of the dependencies were resolved. I'm sure it will be the same through terminal.

4.2 is the most recent version, and seems very stable on my system at the moment.

---

### Post by Mad_Max_1412 on 2009-02-20
Hi

I tried the suggestion and below is the result - as you can see, I answered "n" to the first question and the "q" to the second.  Hope that was right.

> max@ubuntu:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  kdebase-runtime 
The following NEW packages will be installed:
  adept akregator apport-qt ark dragonplayer foomatic-db-gutenprint gnupg-agent gtk-qt-engine 
  guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint{a} jockey-kde kaddressbook kamera kate 
  kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin{a} kdebase-data{a} kdebase-plasma 
  kdebase-workspace-bin kdebase-workspace-data{a} kdebase-workspace-libs4+5{a} kdebluetooth 
  kdegraphics-strigi-plugins kdemultimedia-kio-plugins kdepasswd kdepim-kresources{a} kdepim-strigi-plugins 
  kdepim-wizards kdepimlibs-data{a} kdepimlibs5{a} kdeplasma-addons kdeplasma-addons-data{a} 
  kdeplasma-addons-libs4{a} kdm kgrubeditor klipper kmag kmail kmix kmousetool knotes{a} konqueror 
  konqueror-nsplugins{a} konqueror-plugin-searchbar konsole kontact konversation kopete korganizer{a} krdc 
  krfb ksnapshot ksysguard ksysguardd{a} ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash 
  kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd 
  kwalletmanager language-selector-qt libakonadiprivate1{a} libboost-program-options1.34.1{a} libcapseo0{a} 
  libcaptury0{a} libdbus-1-qt3{a} libgeoip1{a} libkcddb4{a} libkdecorations4{a} libkdepim4{a} 
  libkholidays4{a} libkipi-common{a} libkipi5{a} libkleo4{a} libkpgp4{a} libksieve4{a} libkwineffects1{a} 
  libmimelib4{a} libokularcore1{a} libplasma2{a} libpoppler-qt4-3{a} libqca2{a} libqca2-plugin-ossl{a} 
  libqimageblitz4{a} libqt4-core{a} libsearchclient0{a} libstrigihtmlgui0{a} libvncserver0{a} libzip1{a} 
  mediamanager network-manager-kde okular okular-extra-backends openoffice.org-kde 
  openoffice.org-style-crystal{a} oxygen-cursor-theme phonon-backend-xine pinentry-gtk2{a} pinentry-qt4 
  plasmoid-quickaccess python-qt3{a} python-qt4-dbus{a} python-reportlab{a} software-properties-kde 
  speedcrunch strigi-client strigi-daemon{a} system-config-printer-kde systemsettings ttf-dustin{a} 
  update-manager-kde{a} update-notifier-kde{a} 
The following packages will be REMOVED:
  discover1-data{u} kde-icons-oxygen{a} setserial{u} 
0 packages upgraded, 122 newly installed, 3 to remove and 0 not upgraded.
Need to get 75.9MB of archives. After unpacking 286MB will be used.
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kde-icons-oxygen (>= 4:4.1.4-0ubuntu1~intrepid1) but it is not installable
The following actions will resolve these dependencies:

Install the following packages:
phonon-backend-xine [4:4.1.4-0ubuntu1~intrepid1 (intrepid-updates)]

Keep the following packages at their current version:
kde-icons-oxygen [4:4.1.4-0ubuntu1~intrepid1 (intrepid-updates, now)]

Leave the following dependencies unresolved:
python-reportlab recommends python-renderpm
Score is -49

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

Install the following packages:
phonon-backend-xine [4:4.1.2-0ubuntu6 (intrepid)]

Keep the following packages at their current version:
kde-icons-oxygen [4:4.1.4-0ubuntu1~intrepid1 (intrepid-updates, now)]

Leave the following dependencies unresolved:
python-reportlab recommends python-renderpm
Score is -49

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
 

---

