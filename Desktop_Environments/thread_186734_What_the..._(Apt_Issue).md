---
title: "What the... (Apt Issue)"
date: 2006-06-02
forum: Desktop Environments
---

### Post by shaul26 on 2006-06-02
Yesterday I tried to install some app, but because I had problems I didn't..
So today I try to apt-get install a new app and it told me to try "apt-get -f install" to recover or something like that.. so I did typed it in the terminal..
but...

```

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  brltty brltty-x11 language-selector-common lesstif2 libatspi1.0-0 libbeagle0
  libbrlapi1
Suggested packages:
  libbrlapi1-dev festival brltty-flite
The following packages will be REMOVED:
  abuse abuse-frabs acpi-support amarok amarok-xine amule amule-common apt
  apt-utils aptitude aspell aspell-en audacious audacity beep-media-player
  billard-gl bittornado-gui bluez-cups build-essential cdrdao cmt cupsys
  cupsys-driver-gutenprint dselect dvd+rw-tools dvdrip ecasound ekiga evince
  fbdesk ffmpeg firefox firefox-gnome-support fluxbox foobillard
  foomatic-db-hpijs freeglut3 g++ g++-4.0 gaim gaim2.0 gdm gedit gksu
  gnome-app-install gnome-cups-manager gnome-games gnome-media
  gnome-netstatus-applet gnome-power-manager gnome-spell gnome-system-monitor
  gnome-volume-manager gnomebaker gparted groff-base gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.8-dirac gstreamer0.8-faac
  gstreamer0.8-faad gstreamer0.8-lame gstreamer0.8-misc gstreamer0.8-pitfdll
  gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-sid
  gstreamer0.8-vorbis gstreamer0.8-x gstreamer0.8-xvid hpijs hplip hwdb-client
  kasablanca kcontrol kdebase-bin kdebase-kio-plugins kdelibs-bin kdelibs4c2a
  kdesktop kfind kftpgrabber kicker kmldonkey kmplayer kmplayer-base konqueror
  konsole ksubtile kvirc kvirc-data language-selector language-support-en
  libakode2 libarts1c2a libaspell15 libavahi-qt3-1 libavcodeccvs51
  libavifile-0.7c2 libavutilcvs49 libbinio1c2 libcrypto++5.2c2a
  libdbus-qt-1-1c2 libdc0c2 libdirac0c2a libdjvulibre15 libfaac0 libflac++5c2
  libgc1c2 libgksu1.2-1 libgksuui1.0-1 libglademm-2.4-1c2a libgle3 libglew1
  libglibmm-2.4-1c2a libglu1-mesa libglut3 libgnomecupsui1.0-1c2a
  libgtkmm-2.4-1c2a libgtkspell0 libid3-3.8.3c2a libkonq4 libmjpegtools0c2a
  libmodplug0c2 libmp4v2-0 libmusicbrainz4c2a libmyspell3c2 libopal-2.2.0
  libopenal0 libopenexr2c2a libpoppler0c2 libpoppler0c2-glib libpostproccvs51
  libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2
  libqt3-mt libsdl-sound1.2 libsidplay1 libsigc++-2.0-0c2a libsmpeg0
  libstdc++6 libstdc++6-4.0-dev libstlport4.6c2 libtag1c2a libtunepimp-bin
  libtunepimp2c2a libuniconf4.2 libwpd8c2a libwvstreams4.2-base
  libwvstreams4.2-extras libwxgtk2.4-1 libwxgtk2.6-0 libxine-main1
  libxplc0.3.13 licq licq-plugin-kde licq-plugin-qt lmms lshw man-db menu
  mesa-utils mkvtoolnix mldonkey-server mozilla-firefox-locale-en-gb
  mozilla-mplayer mplayer-386 muse nautilus-cd-burner openoffice.org2
  openoffice.org2-base openoffice.org2-calc openoffice.org2-common
  openoffice.org2-core openoffice.org2-draw openoffice.org2-evolution
  openoffice.org2-gnome openoffice.org2-impress openoffice.org2-l10n-en-us
  openoffice.org2-math openoffice.org2-writer p7zip pekwm
  powermanagement-interface python-apt python-gnome2-desktop
  python-gnome2-extras python-id3lib python-uno python-wxgtk2.6 python2.4-apt
  python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-id3lib qobex
  rhythmbox rss-glx rufus serpentine sound-juicer subtitleeditor synaptic
  telnet thoggen toshset totem totem-gstreamer transcode ubuntu-desktop
  ubuntu-minimal ubuntu-standard update-manager update-notifier valknut
  vbaexpress visualboyadvance vlc vlc-plugin-alsa w3m wvdial wxvlc
  x-window-system-core xbase-clients xine-ui xpdf xpdf-reader xpdf-utils
  xscreensaver-gl xvncviewer yelp
The following NEW packages will be installed:
  brltty brltty-x11 language-selector-common lesstif2 libatspi1.0-0 libbeagle0
  libbrlapi1
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libstdc++6 (due to apt)
0 upgraded, 7 newly installed, 234 to remove and 240 not upgraded.
2 not fully installed or removed.
Need to get 0B/1721kB of archives.
After unpacking 786MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]


```

Why does it want to remove all the software installed? I don't understand what's wrong

---

### Post by mat1t on 2006-06-02
what application were you trying to install?

---

### Post by shaul26 on 2006-06-02
I wanted to install mkvtoolnix but I needed to install a new version of libstdc++6 and gcc-4.1 base... I don't remember if I installed them or not..

---

### Post by PriceChild on 2006-06-02
Whoa you definately don't want to continue with that....

Did the update manager suggest you isntall this? Or are you trying to install your own debs from else where?

Using only official repos?

---

### Post by angkor on 2006-06-02
Can you please post your /etc/apt/sources.list?

---

### Post by shaul26 on 2006-06-02
[QUOTE=PriceChild]Whoa you definately don't want to continue with that....

Did the update manager suggest you isntall this? Or are you trying to install your own debs from else where?

Using only official repos?[/QUOTE]

I tried to install from debs i found on the net...



> Can you please post your /etc/apt/sources.list?
```


# deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060217.2)]/ dapper main restricted 


deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060217.2)]/ dapper main restricted 

# Line commented out by installer because it failed to verify:
# deb http://il.archive.ubuntu.com/ubuntu/ dapper main restricted 
# Line commented out by installer because it failed to verify:
# deb-src http://il.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://il.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
# deb-src http://il.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://il.archive.ubuntu.com/ubuntu/ dapper universe 
# deb-src http://il.archive.ubuntu.com/ubuntu/ dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiversedeb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted 
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu/ dapper-security main restricted 
# deb http://security.ubuntu.com/ubuntu/ dapper-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ dapper-security universe 

deb http://vdlinux.sourceforge.jp/ experimental audacious 
deb-src http://vdlinux.sourceforge.jp/ experimental audacious 

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 
deb http://debian.speedblue.org/ ./ 

deb http://idefix.eup.uva.es/paquetes/gaim2.0/ ./ 
deb http://il.archive.ubuntu.com/ubuntu/ breezy multiverse 

deb http://blacklord.littleboboy.net/debian/ unstable/ 

deb http://apt.agnula.org/demudi/ testing local 
deb-src http://apt.agnula.org/demudi/ testing local 

deb ftp://ftp.nerim.net/debian-marillat/ sarge main 

deb http://wine.lowvoice.nl/apt/ breezy main 
deb-src http://wine.lowvoice.nl/apt/ breezy main 

deb http://www.grawert.net/ubuntu/ warty universe 


```


Thanks for the help :)

---

### Post by Rackerz on 2006-06-02
Your running Dapper Alpha? Have you upgraded to the final yet?

---

### Post by shaul26 on 2006-06-02
[QUOTE=Rackerz]Your running Dapper Alpha? Have you upgraded to the final yet?[/QUOTE]

I'm always updating my ubuntu... Can I upgrade without delete anything? I mean I'm using fluxbox and I made many changes and I'm not sure If i'll remember how to do that stuff again..

---

### Post by Rackerz on 2006-06-02
Run 'update-manager -d' and see if it says anything about updating to 6.06 LTS.

---

### Post by shaul26 on 2006-06-02
[QUOTE=Rackerz]Run 'update-manager -d' and see if it says anything about updating to 6.06 LTS.[/QUOTE]

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

:(

---

### Post by Rackerz on 2006-06-02
I think your sources.list is a little broken. I'm just guessing.

Try this sources.list; 

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

See what happens now.

---

### Post by shaul26 on 2006-06-02
[QUOTE=Rackerz]I think your sources.list is a little broken. I'm just guessing.

Try this sources.list; 



See what happens now.[/QUOTE]

Still having the problem...

---

### Post by Rackerz on 2006-06-02
I can't say I'd be of any more help, try going into the #Ubuntu IRC channel on Freenode, they are usually very helpful.

---

### Post by angkor on 2006-06-02
[QUOTE=shaul26]Still having the problem...[/QUOTE]

Hrm, strange...You did do:

```
sudo apt-get update
```

after changing your sources.list?

and then:

```
sudo apt-get dist-upgrade
```

I don't know what exactly is wrong, but you do have an awful lot of 3rd party repositories in your list. My guess is that some of these aren't compatible with others.

---

### Post by shaul26 on 2006-06-02
[QUOTE=angkor]Hrm, strange...You did do:

```
sudo apt-get update
```

after changing your sources.list?

and then:

```
sudo apt-get dist-upgrade
```

I don't know what exactly is wrong, but you do have an awful lot of 3rd party repositories in your list. My guess is that some of these aren't compatible with others.[/QUOTE]

It's not a problem with the sources list because I didn't change it since last month.. It started only after I installed some deb packages i found on the net...

---

### Post by angkor on 2006-06-02
[QUOTE=shaul26]It's not a problem with the sources list because I didn't change it since last month.. It started only after I installed some deb packages i found on the net...[/QUOTE]

Can't you remove these .debs and try again?

---

### Post by shaul26 on 2006-06-02
[QUOTE=angkor]Can't you remove these .debs and try again?[/QUOTE]

No.. because when I try to remove it says to run sudo apt-get -f install.. and when I'm doing this.... read the first post..

---

### Post by PriceChild on 2006-06-02
Start up synaptic.

At the bottom left, click "custom" Then choose the "Broken" option on the left hand side list.

If there are any packages there with red squares next to them, report them to us please.... you will probably have to remove them.

---

### Post by shaul26 on 2006-06-02
libstdc++6
mkvtoolnix

but when I try to remove them it marked all the app installed on the computer for uninstallation...

---

### Post by PriceChild on 2006-06-02
[quote=shaul26]libstdc++6
mkvtoolnix[/quote]

These are appearing as broken?

---

### Post by angkor on 2006-06-03
I'm wondering if you can remove these packages using 'dpkg -r' and then reinstalling libstdc++6 (repo version of course) using synaptic.

Better backup any important data you have though, cause I have no idea if this is going to have any side effects.

---

### Post by RavenOfOdin on 2006-06-03
[QUOTE=shaul26]```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

:([/QUOTE]

I'm getting that too.

When I try to run the requested command, it says "pkgResolver::Resolve() is unable to fix help dependencies. Unable to correct dependencies."

This is happening with libc6, libc6-dev, belocs-locales-bin, zic, and locales.

Bunches of packages still need to remove themselves so I'm going to have to get the index working again before removal.

And WHY THE HECK does the update-manager shoot one line past the terminal which says "FutureWarning: Apt API not stable" ?!?

If it isn't stable, say so in the damned GUI so people can actually SEE the notification before going ahead and using the tool!

If I had used something other than update-manager I wouldn't be in this mess right now.

I'm going to try to install those packages from the packages.ubuntu.com mirror of itanix.rutgers.edu . . .is this a safe thing to do, both as a practice of installing from third-party mirrors, and as with the -upgrade and --ignore-hold options?  Or should I wait until the index is repaired?

---

