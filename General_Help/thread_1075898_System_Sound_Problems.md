---
title: "System Sound Problems"
date: 2009-02-20
forum: General Help
---

### Post by cyberbob25 on 2009-02-20
First, let me apologize if this has been posted elsewhere.  I did a couple of searches and wasn't able to find anything relevant that worked for me.

I am running Kubuntu Intrepid on an HP Pavilion dv9500.  Everything has been running fine since I installed Intrepid in early November.  

Last night, adept prompted me that there were several updates available.  Here's where things get very bad.  I will admint, I didn't look through the list of updates before letting the updater go.  Anyway, many minutes later, it prompted me about needing to restart the kdm process.  I thought that that was very strange and clicked on cancel.  I then wrapped up my work and shut my laptop off.

After booting it up the next time, I could not get X up and running at all.  After replacing xorg.conf with a backup, I was able to get KDE to a login prompt, but was unable to login, due a lack of an .xsession file.  To remedy this, I installed the kubuntu-desktop package (which then installed what seems like all KDE packages as dependancies).  After this, I was able to login fine, and almost everything working fine.

The problem now is that I cannot get system notifications (or Kopete) working.  All other sound is working fine.  Under system settings=>notifications=>Player Settings tab, I've verified that "Use the KDE Sound System" is checked and the volume is turned all the way up (notifications DO work if I use the external player option and send to vlc or amarok).  

Under system settings=>sound, I do not show any output devices listed for any of the settings on the left.  I don't know if this means anything or not.

Lastly, I've noticed that if I run apt-get upgrade, I receive the following error:

```
The following packages have been kept back:
  phonon-backend-xine
```

I don't know what this means, but from some of the research that I have done, phonon is related to some of the back-end sound system.


Anybody have any ideas?

---

### Post by Woody1987 on 2009-02-20
You will probably need to install this, try sudo apt-get dist-upgrade

---

### Post by cyberbob25 on 2009-02-20
No luck.  

broberts@broberts-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  phonon-backend-xine
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Woody1987 on 2009-02-20
try sudo apt-get install phonon-backend-xine

---

### Post by cyberbob25 on 2009-02-20
I had attempted that at one point, but got scared and backed off.  Here's why
:

broberts@broberts-laptop:~$ sudo apt-get install phonon-backend-xine
sudo: unable to resolve host broberts-laptop
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkipi-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adept akregator ark dolphin dragonplayer gdebi-kde guidance-power-manager gwenview
  install-package jockey-kde kaddressbook kamera kate kde-icons-oxygen kde-printer-applet
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-workspace-bin kdebase-workspace-libs4+5 kdebluetooth
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards
  kdeplasma-addons kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper
  kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar
  konsole kontact kopete korganizer krdc krfb kscreensaver kscreensaver-xsavers ksnapshot
  ksysguard ksystemlog ktimetracker ktorrent kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libkcddb4
  libkdecorations4 libkdepim4 libkholidays4 libkipi5 libkleo4 libkonq5 libkpgp4 libksieve4
  libkwineffects1 libmimelib4 libokularcore1 libplasma2 okular okular-extra-backends
  plasmoid-quickaccess python-kde4 software-properties-kde systemsettings update-manager-kde
  update-notifier-kde xorg
The following packages will be upgraded:
  phonon-backend-xine
1 upgraded, 0 newly installed, 88 to remove and 0 not upgraded.
Need to get 0B/156kB of archives.
After this operation, 180MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by Woody1987 on 2009-02-20
yea that doesnt look good, it looks like you may have broken it badly. You could try installing it and then install kubuntu-desktop again to reinstall everything it removed, but that might not work.

---

