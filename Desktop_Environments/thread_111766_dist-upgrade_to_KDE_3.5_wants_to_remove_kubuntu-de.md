---
title: "dist-upgrade to KDE 3.5 wants to remove kubuntu-desktop etc."
date: 2006-01-02
forum: Desktop Environments
---

### Post by burningbed on 2006-01-02
Can anybody tell me why kubuntu-desktop is scheduled for removal when trying to dist-upgrade to KDE 3.5? I understand that kubuntu-desktop is just a meta-package, but I'd like to keep it or at least understand why it's being uninstalled. All I did was add the following repositories and run apt-get update:

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
deb-src [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

Here's the output:
```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  akode akode-mpeg kubuntu-desktop libkcal2a libkdeedu1 libkdepim1 libkleopatra0a libmimelib1a
The following NEW packages will be installed:
  kdepim-kresources kfaxview libakode2 libarts1-akode libgnokii2 libkcal2b libkdeedu3 libkdepim1a libkleopatra1 libkmime2 libmad0-dev libmimelib1c2 perl-suid
The following packages have been kept back:
  kdeedu
The following packages will be upgraded:
  akregator ark arts artsbuilder atlantik atlantikdesigner cervisia dcoprss juk kaboodle kaddressbook kaddressbook-plugins kalzium kamera kandy kappfinder kapptemplate karm
  kate kate-plugins kaudiocreator kbabel kbabel-dev kbruch kbugbuster kcachegrind kcachegrind-converters kcalc kcharselect kcoloredit kcontrol kcron kdat kde-i18n-de kdeaddons
  kdeaddons-doc-html kdeaddons-kfile-plugins kdeadmin kdeadmin-doc-html kdeadmin-kfile-plugins kdeartwork-misc kdebase kdebase-bin kdebase-data kdebase-dev kdebase-doc-html
  kdebase-kio-plugins kdeedu-data kdeedu-doc-html kdegraphics kdegraphics-doc-html kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs-data kdelibs4-dev kdelibs4-doc
  kdelibs4c2 kdelirc kdemultimedia kdemultimedia-dev kdemultimedia-doc-html kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-doc-html kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint kdesdk kdesdk-doc-html
  kdesdk-kfile-plugins kdesdk-misc kdesdk-scripts kdesktop kdessh kdeutils kdeutils-doc-html kdevelop3 kdevelop3-data kdevelop3-doc kdevelop3-plugins kdewebdev-doc-html kdf
  kdict kdm kdvi kedit keduca kfax kfilereplace kfind kfloppy kgamma kget kghostview kgpg khangman khelpcenter khexedit kicker kicker-applets kiconedit kig kimagemapeditor
  kitchensync kiten kjots klaptopdaemon klatin klettres klettres-data klinkstatus klipper kmail kmenuedit kmid kmilo kmix kmplot kmrml kmtrace knetworkconf knewsticker
  knewsticker-scripts knode knotes kolourpaint kommander kompare konq-plugins konqueror konqueror-nsplugins konsole kontact kooka kopete korganizer kpackage kpager kpdf
  kpercentage kpersonalizer kpf kpilot kpovmodeler kppp krdc krec kregexpeditor krfb kruler kscd kscreensaver ksig ksim ksirc ksmserver ksnapshot ksplash kspy kstars
  kstars-data ksvg ksysguard ksysguardd ksysv ktalkd ktimer ktip ktouch kttsd kttsd-contrib-plugins kturtle kuickshow kuiviewer kuser kverbos kview kviewshell kvoctrain
  kwalletmanager kwifimanager kwin kwordquiz kworldclock kxsldbg libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine libarts1c2 libartsc0 libartsc0-dev
  libcvsservice0 libkcddb1 libkdegames1 libkiten1 libkonq4 libkonq4-dev libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 librss1 lisa mpeglib networkstatus
  noatun noatun-plugins poxml quanta quanta-data secpolicy superkaramba umbrello
222 upgraded, 13 newly installed, 8 to remove and 1 not upgraded.
Need to get 190MB of archives.
After unpacking 213MB disk space will be freed.
Do you want to continue [Y/n]?

```

If I just do a plain upgrade several important packages are being kept back ... why?

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  akregator ark arts artsbuilder atlantik atlantikdesigner cervisia dcoprss juk kaboodle kaddressbook kaddressbook-plugins kalzium kamera kandy kappfinder karm kate
  kate-plugins kaudiocreator kbabel kbabel-dev kbruch kbugbuster kcachegrind kcalc kcharselect kcoloredit kcontrol kcron kdat kde-i18n-de kdeaddons kdeaddons-kfile-plugins
  kdeadmin kdeadmin-kfile-plugins kdebase kdebase-bin kdebase-dev kdebase-kio-plugins kdeedu kdegraphics kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4-dev kdelibs4c2
  kdelirc kdemultimedia kdemultimedia-dev kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-wizards kdeprint kdesdk kdesdk-kfile-plugins kdesdk-misc kdesktop kdessh kdeutils kdevelop3 kdevelop3-data kdevelop3-plugins
  kdf kdict kdm kdvi kedit keduca kfax kfilereplace kfind kfloppy kgamma kget kghostview kgpg khangman khelpcenter khexedit kicker kicker-applets kiconedit kig kimagemapeditor
  kitchensync kiten kjots klaptopdaemon klatin klettres klettres-data klinkstatus klipper kmail kmenuedit kmid kmilo kmix kmplot kmrml kmtrace knetworkconf knewsticker knode
  knotes kolourpaint kommander kompare konq-plugins konqueror konqueror-nsplugins konsole kontact kooka kopete korganizer kpackage kpager kpdf kpercentage kpersonalizer kpf
  kpilot kpovmodeler kppp krdc krec kregexpeditor krfb kruler kscd kscreensaver ksig ksim ksirc ksmserver ksnapshot ksplash kspy kstars kstars-data ksvg ksysguard ksysguardd
  ksysv ktalkd ktimer ktip ktouch kttsd kttsd-contrib-plugins kturtle kuickshow kuiviewer kuser kverbos kview kviewshell kvoctrain kwalletmanager kwifimanager kwin kwordquiz
  kworldclock kxsldbg libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine libarts1c2 libartsc0 libartsc0-dev libcvsservice0 libkcddb1 libkdegames1 libkiten1
  libkonq4 libkonq4-dev libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 librss1 lisa mpeglib networkstatus noatun noatun-plugins quanta quanta-data
  secpolicy superkaramba umbrello
The following packages will be upgraded:
  kapptemplate kcachegrind-converters kdeaddons-doc-html kdeadmin-doc-html kdeartwork-misc kdebase-data kdebase-doc-html kdeedu-data kdeedu-doc-html kdegraphics-doc-html
  kdelibs-data kdelibs4-doc kdemultimedia-doc-html kdemultimedia-kappfinder-data kdenetwork-doc-html kdesdk-doc-html kdesdk-scripts kdeutils-doc-html kdevelop3-doc
  kdewebdev-doc-html knewsticker-scripts poxml
22 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
Need to get 21.7MB of archives.
After unpacking 249MB disk space will be freed.
Do you want to continue [Y/n]?

```

Will this change when KDE 3.5.1 comes out (January 20?)?

---

### Post by Iandefor on 2006-01-02
As for using dist-upgrade: I imagine it's probably because kubuntu-desktop stipulates whatever version of KDE came with Kubuntu; since you'll be removing it and installing a new version, it sees that the system is changing in a way that will bugger the depenencies up (even though kubuntu-desktop is a metapackage, it doesn't know that) and so it removes the packages that will be negatively influenced by not having their dependencies met. Just a suspicion, though.

---

### Post by sharke on 2006-01-03
i used the same sources . what i did was sudo apt-get upgrade this had the same result pakages not upgraded. I then opened synaptic and selected mark all upgrades after this finished i had problems with lib dependences so back to terminal sudo apt-get -f install this uninstalled the problem libs amd installed correct versions .
kde 3.5 now working fine
Regards
Sharke

---

### Post by burningbed on 2006-01-03
So do you now have kubuntu-desktop installed or not?

---

### Post by JamesNorris on 2006-01-03
[QUOTE=sharke]i used the same sources . what i did was sudo apt-get upgrade this had the same result pakages not upgraded. I then opened synaptic and selected mark all upgrades after this finished i had problems with lib dependences so back to terminal sudo apt-get -f install this uninstalled the problem libs amd installed correct versions .
kde 3.5 now working fine
Regards
Sharke[/QUOTE]


That's how I had to do it, too, so I think that's normal. I had to 'upgrade' '-f install' and then 'upgrade' again before I got it working. I still have the kubuntu-desktop installed, too. :)

---

### Post by branco on 2006-01-03
I did it with Aptutude... I just checked all the violet items (the ones that were scheduled for removal) for missing dependencies and installed them all. Works quite nicely. :D

---

