---
title: "KDE stealing space"
date: 2009-03-02
forum: Desktop Environments
---

### Post by bgs100 on 2009-03-02
I installed kde with:
```
sudo aptitude install kde
```
It said 698mb would be used
About 30 minutes later, it was done, so I restarted and selected it as my session.
Well, I had a few problems with KDE, so uninstalled.
```
sudo aptitude purge kde
```
But when it went to uninstall, it only said 5-hundred-something mb would be freed.

What happened to this extra space?

---

### Post by taurus on 2009-03-02
```
sudo aptitude autoremove
```

---

### Post by perpetualcacophany on 2009-03-02
I think [this](http://www.psychocats.net/ubuntu/puregnome) site might help you. I actually just tried out kde too and used this to figure out how to get back to just gnome and all of its associated standard programs.

---

### Post by bgs100 on 2009-03-03
> **taurus said:**
> ```
sudo aptitude autoremove
```

aptitude has no autoremove command, and apt-get autoremove did nothing

> **perpetualcacophany said:**
> I think [this](http://www.psychocats.net/ubuntu/puregnome) site might help you. I actually just tried out kde too and used this to figure out how to get back to just gnome and all of its associated standard programs.

Well, this ended up wanting to remove some of my applications like:
```

The following packages will be REMOVED:
  avidemux avidemux-common ekiga exfalso ffmpeg foomatic-db-gutenprint
  frozen-bubble gnome-art gnome-splashscreen-manager gstreamer0.10-plugins-bad
  ijsgutenprint imagemagick iriverter kde-icons-oxygen kde-window-manager
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdelibs-bin kdelibs5 kdelibs5-data khelpcenter4
  lbreakout2 lbreakout2-data libaprutil1 libart2-ruby1.8 libartsc0
  libartsc0-dev libatk1-ruby1.8 libaudio-dev libaudio2 libcairo-ruby1.8
  libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-1-qt3-dev
  libfftw3-3 libgconf2-ruby libgconf2-ruby1.8 libgdk-pixbuf2-ruby1.8
  libglade2-ruby libglade2-ruby1.8 libglib2-ruby1.8 libgmyth0 libgnome2-ruby
  libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 libgtk2-ruby1.8 libkdecorations4
  libkwineffects1 libmodplug0c2 libmpcdec3 libmysqlclient15off libofa0
  libopal-2.2 libpango1-ruby1.8 libphonon4 libpq5 libpt-1.10.10 libqt3-mt
  libqt3-mt-dev libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-xml libqtcore4 libqtgui4 libraptor1
  librasqal0 librdf0 libruby1.8 libsdl-console libsdl-gfx1.2-4 libsdl-image1.2
  libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-net1.2
  libsdl-pango1 libsdl-perl libsdl-sound1.2 libsdl-sound1.2-dev
  libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev libsdl1.2debian
  libsdl1.2debian-all libsmpeg-dev libsmpeg0 libsoprano4 libstreamanalyzer0
  libstreams0 libstrigiqtdbusclient0 libsvn1 libxine1-bin libxine1-ffmpeg
  libxvmc1 mencoder mjpegtools moc mozilla-mplayer mplayer mysql-common phonon
  phonon-backend-gstreamer printconf python-qt4-dbus qemu qemu-launcher
  qt3-dev-tools qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 smplayer
  smplayer-themes soprano-daemon stopmotion subversion supertux-stable wormux
0 upgraded, 0 newly installed, 131 to remove and 8 not upgraded.
After this operation, 390MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```
I like many of the applications listed above, like avidemux, lbreakout2, exfalso, ffmpeg, and so on.  And I don't usually trust huge remove commands. Dependencies get caught up easily.

---

