---
title: "the &quot;Foremost&quot; file recovery program deleted a lot of packages during install"
date: 2009-04-20
forum: General Help
---

### Post by szenith on 2009-04-20
stupidly I don't have the list because I was messing around in the terminal and closed it for dumb reason, but "Foremost" [http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html) happened to delete about 260 megabytes worth of packages when I typed "sudo aptitude install foremost" without looking at what it said and pressing "y". 

should I be worried about this? it seemed to delete a whole lot of stuff, so I'm wondering if anyone is familiar with what exactly it deletes for the program to be installed, and how important those packages are in regards to ubuntu and how it will run. Sorry I'm fairly new to linux, and I don't have the log files to tell you what it deleted, but if anyone is familiar with the program it would be nice to know what it deleted. Thank you!

---

### Post by hikaricore on 2009-04-20
First of all you probably should reinstall the packages you removed if you're worried.
Second use apt-get in the future if you don't know what you're doing.

---

### Post by szenith on 2009-04-20
> **hikaricore said:**
> First of all you probably should reinstall the packages you removed if you're worried.
Second use apt-get in the future if you don't know what you're doing.

I don't have the log of the packages it removed.. that's the thing, also what's the difference between apt-get and aptitude?

---

### Post by szenith on 2009-04-20
is there a general way to reinstall the regular stuff that's on Ubuntu from a fresh install?

---

### Post by szenith on 2009-04-20
Actually, luckily I ended up doing a google search with the stuff that it uninstalled hoping someone I had a log, so I was able to find this in my google history

Removing dvgrab ... Removing exiv2 ... Removing ffmpeg ... Removing vgrabbj ... Removing ftplib3 ... Removing kdemultimedia-kio-plugins ... Removing libkcddb4 ... Removing khelpcenter4 ... Removing kdelibs4c2a ... Removing kdelibs-data ... Removing libavahi-qt3-1 ... Removing libavdevice52 ... Removing libavfilter0 ... Removing orange ... Removing liborange0 ... Removing libdynamite0 ... Removing libloudmouth1-0 ... Removing liblualib50 ... Removing liblua50 ... Removing libqt4-webkit ... Removing phonon ... Removing redland-utils ... Removing qt4-qtconfig ... Removing libqt4-opengl ... Removing libqt4-sql-mysql ... Removing libqt4-test ... Removing ruby ... Removing ruby1.8 ... Removing libruby1.8 ... Removing libsdl-image1.2 ... Removing libsynce0 ... Removing libtar ... Removing libunshield0 ... Removing kdebase-runtime ... Removing kdebase-runtime-bin-kde4 ... Removing kde-icons-oxygen ... Removing kdebase-runtime-data ... Removing kdebase-runtime-data-common ... Removing kdelibs5 ... Removing kdelibs5-data ... Removing libstreamanalyzer0 ... Removing libexiv2-5 ... Removing phonon-backend-xine ... Removing libphonon4 ... Removing libqt4-qt3support ... Removing libqt4-designer ... Removing libqt4-sql ... Removing libstreams0 ... Removing libxine1 ... Removing libxine1-x ... Removing libxcb-shape0 ... Removing libxcb-shm0 ... Removing libxcb-xv0 ... Removing libxine1-misc-plugins ...

so I think that's all the stuff it removed

---

### Post by szenith on 2009-04-20
okay im currently re-downloading those packages, lucky that i had it saved in a search, would be interested to know why Foremost decided to delete all that stuff

---

### Post by hikaricore on 2009-04-21
Because you used aptitude and just blindly hit yes.
There's probably a package conflict somewhere in there.

---

