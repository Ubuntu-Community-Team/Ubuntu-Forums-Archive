---
title: "how to update to kde 3.5?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by zojas on 2005-11-29
I'm running breezy, ran apt-get update, and then tried apt-get upgrade, but there weren't any kde packages to update. how do I get the new kde 3.5 release?

thanks.

---

### Post by ltmon on 2005-11-29
3.5 won't be released as an official Breezy update.  To get it you need to add extra repositories.

see: [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

---

### Post by zojas on 2005-11-29
thanks.

---

### Post by zojas on 2005-11-29
I updated using that repository, but 'about kde' still reports kde 3.4.3. what's going on?

---

### Post by sanguinemoon on 2005-11-29
Did you restart the X server?

---

### Post by cowlip on 2005-11-29
Hi, pres ctrl + alt + backspace on your keybaord (warning: log out b4 doing this)

---

### Post by zojas on 2005-11-30
tried that, no good. 

when I did the upgrade, it told me this:

```

The following packages have been kept back:
  akregator ark arts artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4-dev
  kdelibs4c2 kdemultimedia-kfile-plugins kdemultimedia-kio-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins
  kdepim-wizards kdeprint kdesktop kdm kfind kghostview khelpcenter kicker
  klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes
  konq-plugins konqueror konqueror-nsplugins konsole kontact kooka kopete
  korganizer kpdf kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot
  ksplash ksvg ksysguard ksysguardd ktuberling kuser kwalletmanager
  kwifimanager kwin language-support-en libarts1-dev libarts1c2 libartsc0
  libartsc0-dev libkcddb1 libkdegames1 libkleopatra0a libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  kdebase-data kdelibs-data kdemultimedia-kappfinder-data
3 upgraded, 0 newly installed, 0 to remove and 83 not upgraded.

```

so I guess I didn't really get kde 3.5 yet?

---

### Post by f1dave on 2005-11-30
Perhaps try doing the upgrade again- it may be it had to update something else before you could upgrade the whole system. Seems odd to me, as mine worked straight off the bat, but you could give it a shot.

---

### Post by zojas on 2005-11-30
I finally got it. a quick google search turned up this:

[http://www.debian-administration.org/articles/69]("http://www.debian-administration.org/articles/69")

basically, I needed to do a dist-upgrade to get it to put on the new dependencies.

---

### Post by abhitux on 2005-11-30
This is for total newbies (like me).

Open up Synaptic. Click properties and add repostories.

You can paste this here in the dialogue
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

Simple. Now reload and walla! All the packages that need to be updated would be displayed in the KDE Desktop window.

On second thoughts, this Ubuntu should default with KDE and Gnome should be after installation.

---

