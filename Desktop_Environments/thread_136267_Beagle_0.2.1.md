---
title: "Beagle 0.2.1"
date: 2006-02-25
forum: Desktop Environments
---

### Post by s_groening on 2006-02-25
I am trying to get Beagle 0.21 to work on 'Breezy', however, I am experiencing problems with Glibc, which does not seem to be available as binary packages in a version >=2.8.5, the latest available being 2.8.3...

I have tried compiling from source, however, this has not been very successful for me, since Mono packages still do not install properly as well as GTK# not installing properly either (relying on libglib-2.8.5)

Is there a 'Dapper' package repository available somwhere that might be of use here?

---

### Post by gunksta on 2006-02-25
Yep, this is in Dapper alright.  But, I wouldn't start replacing something as important as glib without just upgrading.  You're less likely to break something....at least....until it gets broken by someone else in Dapper.  :-)

--andy

---

### Post by Spie on 2006-02-26
Just upgrade to Dapper. It's quite useable now. And Beagle looks very nice! Especially with the Deskbar applet.

---

### Post by rwabel on 2006-02-28
but there is no longer best!? at least I can't find it. do you only use deskbar now?

---

### Post by kaamos on 2006-02-28
best has been replaced with (imho) a LOT better "beagle-search"

---

### Post by rwabel on 2006-02-28
can't find beagle-search? it's not yet in dapper?!

---

### Post by kaamos on 2006-02-28
[packages.ubuntu.com](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=beagle&version=dapper&arch=i386) shows that beagle in dapper comes with best and not beagle-search. Not sure how up-to-date that is though.. Hopefully this will change before release. Strange, I thought that best was dropped completely starting from 0.2.0 and the dapped version is 0.2.1-1ubuntu5

---

### Post by rwabel on 2006-02-28
that's wired. here is my installed files for beagle on my dapper. there is no best around but the package on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) shows it. I've installed also the one from the homepage. no luck.
```
/.
/usr
/usr/bin
/usr/bin/beagled
/usr/bin/beagle-index-url
/usr/bin/beagle-info
/usr/bin/beagle-shutdown
/usr/bin/beagle-query
/usr/bin/beagle-exercise-file-system
/usr/bin/beagle-config
/usr/bin/beagle-settings
/usr/bin/beagle-index-info
/usr/bin/beagle-ping
/usr/bin/beagle-status
/usr/bin/beagle-search
/usr/bin/beagle-imlogviewer
/usr/sbin
/usr/sbin/beagle-build-index
/usr/sbin/beagle-manage-index
/usr/lib
/usr/lib/beagle
/usr/lib/beagle/Util.dll
/usr/lib/beagle/Util.dll.config
/usr/lib/beagle/UiUtil.dll
/usr/lib/beagle/UiUtil.dll.config
/usr/lib/beagle/libbeagleglue.so.0.0.0
/usr/lib/beagle/libbeagleuiglue.so.0.0.0
/usr/lib/beagle/Beagle.dll
/usr/lib/beagle/BeagleDaemonPlugins.dll
/usr/lib/beagle/BeagleDaemonLib.dll
/usr/lib/beagle/BeagleDaemon.exe
/usr/lib/beagle/IndexWebContent.exe
/usr/lib/beagle/IndexHelper.exe
/usr/lib/beagle/beagled-index-helper
/usr/lib/beagle/BuildIndex.exe
/usr/lib/beagle/ManageIndex.exe
/usr/lib/beagle/Filters
/usr/lib/beagle/Filters/Filters.dll
/usr/lib/beagle/Info.exe
/usr/lib/beagle/Shutdown.exe
/usr/lib/beagle/Query.exe
/usr/lib/beagle/ExerciseFileSystem.exe
/usr/lib/beagle/Config.exe
/usr/lib/beagle/Settings.exe
/usr/lib/beagle/Images.dll
/usr/lib/beagle/Search.exe
/usr/lib/beagle/ImLogViewer.exe
/usr/share
/usr/share/doc
/usr/share/doc/beagle
/usr/share/doc/beagle/crawl-system
/usr/share/doc/beagle/crawl-system/bin
/usr/share/doc/beagle/crawl-system/bin/beagle-crawl-system
/usr/share/doc/beagle/crawl-system/etc
/usr/share/doc/beagle/crawl-system/etc/beagle
/usr/share/doc/beagle/crawl-system/etc/beagle/crawl-windows
/usr/share/doc/beagle/crawl-system/etc/beagle/crawl-applications
/usr/share/doc/beagle/crawl-system/etc/beagle/crawl-documentation
/usr/share/doc/beagle/crawl-system/etc/cron.d
/usr/share/doc/beagle/crawl-system/etc/cron.d/beagle-crawl-system.crontab
/usr/share/doc/beagle/mozilla-extension
/usr/share/doc/beagle/changelog.gz
/usr/share/doc/beagle/NEWS.gz
/usr/share/doc/beagle/changelog.Debian.gz
/usr/share/doc/beagle/README
/usr/share/doc/beagle/README.Debian
/usr/share/doc/beagle/copyright
/usr/share/locale
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/beagle.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/beagle.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/beagle.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/beagle.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/beagle.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/beagle.mo
/usr/share/locale/en_CA
/usr/share/locale/en_CA/LC_MESSAGES
/usr/share/locale/en_CA/LC_MESSAGES/beagle.mo
/usr/share/locale/en_GB
/usr/share/locale/en_GB/LC_MESSAGES
/usr/share/locale/en_GB/LC_MESSAGES/beagle.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/beagle.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/beagle.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/beagle.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/beagle.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/beagle.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/beagle.mo
/usr/share/locale/lt
/usr/share/locale/lt/LC_MESSAGES
/usr/share/locale/lt/LC_MESSAGES/beagle.mo
/usr/share/locale/mk
/usr/share/locale/mk/LC_MESSAGES
/usr/share/locale/mk/LC_MESSAGES/beagle.mo
/usr/share/locale/nb
/usr/share/locale/nb/LC_MESSAGES
/usr/share/locale/nb/LC_MESSAGES/beagle.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/beagle.mo
/usr/share/locale/no
/usr/share/locale/no/LC_MESSAGES
/usr/share/locale/no/LC_MESSAGES/beagle.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/beagle.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/beagle.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/beagle.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/beagle.mo
/usr/share/locale/uk
/usr/share/locale/uk/LC_MESSAGES
/usr/share/locale/uk/LC_MESSAGES/beagle.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/beagle.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/beagle.mo
/usr/share/locale/zh_HK
/usr/share/locale/zh_HK/LC_MESSAGES
/usr/share/locale/zh_HK/LC_MESSAGES/beagle.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/beagle.mo
/usr/share/beagle
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/beagle-shutdown.1.gz
/usr/share/man/man1/beagle-status.1.gz
/usr/share/man/man1/beagle-config.1.gz
/usr/share/man/man1/beagled.1.gz
/usr/share/man/man1/beagle-query.1.gz
/usr/share/man/man8
/usr/share/man/man8/beagle-build-index.8.gz
/usr/share/man/man8/beagle-manage-index.8.gz
/usr/share/applications
/usr/share/applications/beagle-settings.desktop
/usr/share/applications/beagle-search.desktop
/usr/share/pixmaps
/usr/share/pixmaps/system-search.png
/usr/lib/beagle/libbeagleglue.so.0
/usr/lib/beagle/libbeagleglue.so
/usr/lib/beagle/libbeagleuiglue.so
/usr/lib/beagle/libbeagleuiglue.so.0
/etc/beagle/crawl-windows
/etc/beagle/crawl-applications
/etc/beagle/crawl-documentation
/etc/cron.d/beagle-crawl-system.crontab
```

---

### Post by browneyedgirl65 on 2006-03-01
I'm confused.  I've got Breezy Badger installed, and I just used synaptic package manager to install beagle, which it did just fine.  It doesn't seem to have best, though.  I do note that inotify seems to be part of the kernel?

Quickie question: for beagled to start up automatically, can I pop it in the system->preferences->sessions startup tab in dialogue box?

---

### Post by rwabel on 2006-03-01
there is also an indexing & search feature in the gnome preferences somewhere. but it's doesn't work as I can remember. but you can put it in the startup to make it start up automatically.

under dapper I guess there is a package called best.

---

