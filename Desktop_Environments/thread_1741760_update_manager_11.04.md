---
title: "update manager 11.04"
date: 2011-04-28
forum: Desktop Environments
---

### Post by imcgee on 2011-04-28
I got this error message when i tried to update to 11.04, anyone got any ideas

After your package information was updated the essential package 'ubuntu-minimal' can not be found anymore. This indicates a serious error, please report this bug against the 'update manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Also, i tried to upload the other files in the directory but the applet wouldnt let me

details below

main.log
2011-04-28 16:51:28,897 INFO Using config files '['./DistUpgrade.cfg']'
2011-04-28 16:51:28,897 INFO uname information: 'Linux subtle 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64'
2011-04-28 16:51:28,898 INFO release-upgrader version '0.150' started
2011-04-28 16:51:29,007 DEBUG svg pixbuf loader failed (Error displaying image)
2011-04-28 16:51:29,098 DEBUG Using 'DistUpgradeViewGtk' view
2011-04-28 16:51:29,130 DEBUG aufsOptionsAndEnvironmentSetup()
2011-04-28 16:51:29,131 DEBUG using '/tmp/upgrade-rw-AuxKkw' as aufs_rw_dir
2011-04-28 16:51:29,132 DEBUG using '/tmp/upgrade-chroot-Sdi2qf' as aufs chroot dir
2011-04-28 16:51:29,132 DEBUG enable dpkg --force-overwrite
2011-04-28 16:51:29,147 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2011-04-28 16:51:30,379 DEBUG lsb-release: 'maverick'
2011-04-28 16:51:30,380 DEBUG _pythonSymlinkCheck run
2011-04-28 16:51:30,391 DEBUG openCache()
2011-04-28 16:51:30,611 DEBUG /openCache(), new cache size 32351
2011-04-28 16:51:30,612 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-04-28 16:51:30,612 DEBUG checkViewDepends()
2011-04-28 16:51:30,612 DEBUG running doUpdate() (showErrors=False)
2011-04-28 16:52:19,318 DEBUG openCache()
2011-04-28 16:52:20,678 DEBUG /openCache(), new cache size 32351
2011-04-28 16:52:20,679 DEBUG doPostInitialUpdate
2011-04-28 16:52:20,679 DEBUG Plugin modules in ./plugins: kdelibs4to5_plugin.py remove_lilo_plugin.py langpack_manual_plugin.py dpkg_status_plugin.py deb_plugin.py
2011-04-28 16:52:20,679 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-04-28 16:52:20,681 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-04-28 16:52:20,681 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-04-28 16:52:20,683 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-04-28 16:52:20,683 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-04-28 16:52:20,684 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-04-28 16:52:20,685 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-04-28 16:52:20,687 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-04-28 16:52:20,687 DEBUG Loading module ./plugins/deb_plugin.py
2011-04-28 16:52:20,688 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-04-28 16:52:20,688 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-04-28 16:52:20,688 DEBUG plugins for condition 'nattyPostInitialUpdate' are '[]'
2011-04-28 16:52:20,688 DEBUG plugins for condition 'from_maverickPostInitialUpdate' are '[]'
2011-04-28 16:52:23,489 DEBUG Foreign: gstreamer0.10-fluendo-plugins-mp3-partner ipheth-utils opensync-plugin-synce librapi2 opera libimobiledevice1 tor libplist1 usbmuxd librapi2-tools synce-sync-engine python-rapi2 libusbmuxd1 libgpod4 tor-geoipdb libsynce0 libgpod-common
2011-04-28 16:52:23,489 DEBUG Obsolete: libobasis3.3-core07 libobasis3.3-core06 libobasis3.3-core05 libobasis3.3-core04 libobasis3.3-core03 libobasis3.3-core02 libobasis3.3-core01 libreoffice3-base libobasis3.3-ooofonts libobasis3.3-extension-report-builder libobasis3.3-math libobasis3.3-calc libobasis3.3-en-us-base libreoffice-debian-menus libobasis3.3-gnome-integration libreoffice3-dict-fr libobasis3.3-en-us libreoffice3-calc libreoffice3-writer libobasis3.3-en-us-writer libobasis3.3-xsltfilter libobasis3.3-kde-integration libobasis3.3-en-us-res libreoffice3-dict-es libreoffice3 libobasis3.3-javafilter libobasis3.3-ooolinguistic libobasis3.3-ogltrans libobasis3.3-extension-mediawiki-publisher libobasis3.3-en-us-math libobasis3.3-extension-presentation-minimizer libreoffice3-dict-en linux-image-2.6.32-25-generic libreoffice3-en-us libobasis3.3-graphicfilter libreoffice3-impress libobasis3.3-testtool libobasis3.3-extension-nlpsolver libobasis3.3-binfilter libopensync0 libobasis3.3-pyuno opensync-module-python libreoffice3-math libobasis3.3-impress libobasis3.3-en-us-binfilter libobasis3.3-extension-presenter-screen libreoffice3-draw libreoffice3-ure mysql-workbench-gpl libobasis3.3-draw libobasis3.3-writer libobasis3.3-extension-pdf-import libobasis3.3-images libobasis3.3-en-us-calc libobasis3.3-base
2011-04-28 16:52:23,490 DEBUG updateSourcesList()
2011-04-28 16:52:23,532 DEBUG rewriteSourcesList()
2011-04-28 16:52:23,534 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted'
2011-04-28 16:52:23,534 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted' updated to new dist
2011-04-28 16:52:23,534 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted'
2011-04-28 16:52:23,535 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty main restricted' updated to new dist
2011-04-28 16:52:23,535 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted'
2011-04-28 16:52:23,535 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted' updated to new dist
2011-04-28 16:52:23,535 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted'
2011-04-28 16:52:23,535 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates main restricted' updated to new dist
2011-04-28 16:52:23,535 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick universe'
2011-04-28 16:52:23,535 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe' updated to new dist
2011-04-28 16:52:23,535 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick universe'
2011-04-28 16:52:23,535 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty universe' updated to new dist
2011-04-28 16:52:23,535 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates universe'
2011-04-28 16:52:23,535 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe' updated to new dist
2011-04-28 16:52:23,535 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates universe'
2011-04-28 16:52:23,535 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates universe' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick multiverse'
2011-04-28 16:52:23,536 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick multiverse'
2011-04-28 16:52:23,536 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty multiverse' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse'
2011-04-28 16:52:23,536 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse'
2011-04-28 16:52:23,536 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates multiverse' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted'
2011-04-28 16:52:23,536 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted'
2011-04-28 16:52:23,536 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted' updated to new dist
2011-04-28 16:52:23,536 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe'
2011-04-28 16:52:23,537 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe' updated to new dist
2011-04-28 16:52:23,537 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe'
2011-04-28 16:52:23,537 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe' updated to new dist
2011-04-28 16:52:23,537 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse'
2011-04-28 16:52:23,537 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse' updated to new dist
2011-04-28 16:52:23,537 DEBUG examining: 'deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner'
2011-04-28 16:52:23,537 DEBUG entry 'deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner' updated to new dist
2011-04-28 16:52:23,537 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse'
2011-04-28 16:52:23,537 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse' updated to new dist
2011-04-28 16:52:23,537 DEBUG examining: 'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main # disabled on upgrade to maverick'
2011-04-28 16:52:23,540 DEBUG entry '# deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) karmic main # disabled on upgrade to maverick disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 16:52:23,540 DEBUG examining: 'deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) maverick main # disabled on upgrade to maverick'
2011-04-28 16:52:23,542 DEBUG entry '# deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) natty main # disabled on upgrade to maverick disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 16:52:23,542 DEBUG examining: 'deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases) disabled on upgrade to maverick'
2011-04-28 16:52:23,544 DEBUG entry '# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases) disabled on upgrade to maverick disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 16:52:23,544 DEBUG examining: 'deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free #Opera Browser (beta releases)'
2011-04-28 16:52:23,546 DEBUG entry '# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free #Opera Browser (beta releases) disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 16:52:23,546 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner'
2011-04-28 16:52:23,546 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner' updated to new dist
2011-04-28 16:52:23,547 DEBUG examining: 'deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) maverick main # disabled on upgrade to maverick'
2011-04-28 16:52:23,549 DEBUG entry '# deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) natty main # disabled on upgrade to maverick disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 16:52:32,796 DEBUG running doUpdate() (showErrors=True)
2011-04-28 16:53:22,327 DEBUG openCache()
2011-04-28 16:53:22,327 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-04-28 16:53:22,686 DEBUG /openCache(), new cache size 2049
2011-04-28 16:53:22,686 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-04-28 16:53:22,687 ERROR No 'ubuntu-minimal' available/downloadable after sources.list rewrite+update
2011-04-28 16:54:02,887 DEBUG abort called
2011-04-28 16:54:02,890 DEBUG openCache()
2011-04-28 16:54:02,890 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-04-28 16:54:04,295 DEBUG /openCache(), new cache size 32351
2011-04-28 16:54:04,310 DEBUG enabling apt cron job

---

### Post by macky66 on 2011-04-28
I got the same error too while trying the upgrade from 10.10 to 11.04.

I've tried to unistall/reinstall ubuntu-minimal but the problem still persists.

Please find below the just created main.log ...

Thank-you

------------------------------------------------------
2011-04-28 21:28:44,664 INFO Using config files '['./DistUpgrade.cfg']'
2011-04-28 21:28:44,664 INFO uname information: 'Linux macless 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686'
2011-04-28 21:28:44,665 INFO release-upgrader version '0.150' started
2011-04-28 21:28:44,799 DEBUG svg pixbuf loader failed (Error displaying image)
2011-04-28 21:28:44,850 DEBUG Using 'DistUpgradeViewGtk' view
2011-04-28 21:28:44,876 DEBUG aufsOptionsAndEnvironmentSetup()
2011-04-28 21:28:44,877 DEBUG using '/tmp/upgrade-rw-flrAMo' as aufs_rw_dir
2011-04-28 21:28:44,878 DEBUG using '/tmp/upgrade-chroot-_F_umM' as aufs chroot dir
2011-04-28 21:28:44,878 DEBUG enable dpkg --force-overwrite
2011-04-28 21:28:44,894 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2011-04-28 21:28:46,688 DEBUG lsb-release: 'maverick'
2011-04-28 21:28:46,689 DEBUG _pythonSymlinkCheck run
2011-04-28 21:28:46,689 DEBUG openCache()
2011-04-28 21:28:46,998 DEBUG /openCache(), new cache size 32335
2011-04-28 21:28:46,998 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2011-04-28 21:28:46,998 DEBUG checkViewDepends()
2011-04-28 21:28:46,999 DEBUG running doUpdate() (showErrors=False)
2011-04-28 21:29:10,474 DEBUG openCache()
2011-04-28 21:29:10,775 DEBUG /openCache(), new cache size 32335
2011-04-28 21:29:10,775 DEBUG doPostInitialUpdate
2011-04-28 21:29:10,776 DEBUG Plugin modules in ./plugins: kdelibs4to5_plugin.py langpack_manual_plugin.py deb_plugin.py remove_lilo_plugin.py dpkg_status_plugin.py
2011-04-28 21:29:10,776 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-04-28 21:29:10,778 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-04-28 21:29:10,778 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-04-28 21:29:10,780 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-04-28 21:29:10,780 DEBUG Loading module ./plugins/deb_plugin.py
2011-04-28 21:29:10,780 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-04-28 21:29:10,780 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-04-28 21:29:10,781 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-04-28 21:29:10,781 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-04-28 21:29:10,782 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-04-28 21:29:10,782 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-04-28 21:29:10,782 DEBUG plugins for condition 'nattyPostInitialUpdate' are '[]'
2011-04-28 21:29:10,782 DEBUG plugins for condition 'from_maverickPostInitialUpdate' are '[]'
2011-04-28 21:29:14,440 DEBUG Foreign: ubuntu-tweak ttf-symbol-replacement nautilus-dropbox acroread virtualbox-4.0 jdownloader uex wine1.2
2011-04-28 21:29:14,440 DEBUG Obsolete: mediainfo-gui libdvdcss2 libmediainfo0 libzen0 divfix++ nerolinux handbrake-gtk
2011-04-28 21:29:14,441 DEBUG updateSourcesList()
2011-04-28 21:29:14,488 DEBUG rewriteSourcesList()
2011-04-28 21:29:14,491 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick main restricted'
2011-04-28 21:29:14,491 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty main restricted' updated to new dist
2011-04-28 21:29:14,491 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick main restricted'
2011-04-28 21:29:14,491 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty main restricted' updated to new dist
2011-04-28 21:29:14,491 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates main restricted'
2011-04-28 21:29:14,491 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-updates main restricted' updated to new dist
2011-04-28 21:29:14,491 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates main restricted'
2011-04-28 21:29:14,491 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-updates main restricted' updated to new dist
2011-04-28 21:29:14,492 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick universe'
2011-04-28 21:29:14,492 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty universe' updated to new dist
2011-04-28 21:29:14,492 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick universe'
2011-04-28 21:29:14,492 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty universe' updated to new dist
2011-04-28 21:29:14,492 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates universe'
2011-04-28 21:29:14,492 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-updates universe' updated to new dist
2011-04-28 21:29:14,492 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates universe'
2011-04-28 21:29:14,492 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-updates universe' updated to new dist
2011-04-28 21:29:14,492 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick multiverse'
2011-04-28 21:29:14,492 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty multiverse' updated to new dist
2011-04-28 21:29:14,492 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick multiverse'
2011-04-28 21:29:14,493 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty multiverse' updated to new dist
2011-04-28 21:29:14,493 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates multiverse'
2011-04-28 21:29:14,493 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-updates multiverse' updated to new dist
2011-04-28 21:29:14,493 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-updates multiverse'
2011-04-28 21:29:14,493 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-updates multiverse' updated to new dist
2011-04-28 21:29:14,493 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner'
2011-04-28 21:29:14,493 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner' updated to new dist
2011-04-28 21:29:14,493 DEBUG examining: 'deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main'
2011-04-28 21:29:14,493 DEBUG entry 'deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main' updated to new dist
2011-04-28 21:29:14,493 DEBUG examining: 'deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main'
2011-04-28 21:29:14,494 DEBUG entry 'deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main' updated to new dist
2011-04-28 21:29:14,494 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-security main restricted'
2011-04-28 21:29:14,494 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-security main restricted' updated to new dist
2011-04-28 21:29:14,494 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-security main restricted'
2011-04-28 21:29:14,494 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-security main restricted' updated to new dist
2011-04-28 21:29:14,494 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-security universe'
2011-04-28 21:29:14,494 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-security universe' updated to new dist
2011-04-28 21:29:14,494 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-security universe'
2011-04-28 21:29:14,494 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-security universe' updated to new dist
2011-04-28 21:29:14,494 DEBUG examining: 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-security multiverse'
2011-04-28 21:29:14,494 DEBUG entry 'deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-security multiverse' updated to new dist
2011-04-28 21:29:14,495 DEBUG examining: 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-security multiverse'
2011-04-28 21:29:14,495 DEBUG entry 'deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty-security multiverse' updated to new dist
2011-04-28 21:29:14,495 DEBUG examining: 'deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib'
2011-04-28 21:29:14,498 DEBUG entry '# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib # disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:14,498 DEBUG examining: 'deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) maverick main #Ubuntu Tweak Stable Source'
2011-04-28 21:29:14,500 DEBUG entry '# deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) natty main #Ubuntu Tweak Stable Source disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:14,501 DEBUG examining: 'deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main'
2011-04-28 21:29:14,503 DEBUG entry '# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main # disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:14,503 DEBUG examining: 'deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main'
2011-04-28 21:29:14,506 DEBUG entry '# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main # disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:14,506 DEBUG examining: 'deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main'
2011-04-28 21:29:14,509 DEBUG entry '# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) natty main # disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:14,509 DEBUG examining: 'deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main'
2011-04-28 21:29:14,512 DEBUG entry '# deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) natty main # disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:14,512 DEBUG examining: 'deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main'
2011-04-28 21:29:14,515 DEBUG entry '# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) natty main # disabled on upgrade to natty' was disabled (unknown mirror)
2011-04-28 21:29:16,623 DEBUG running doUpdate() (showErrors=True)
2011-04-28 21:29:38,529 DEBUG openCache()
2011-04-28 21:29:38,529 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-04-28 21:29:39,065 DEBUG /openCache(), new cache size 2108
2011-04-28 21:29:39,066 DEBUG needServerMode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2011-04-28 21:29:39,066 ERROR No 'ubuntu-minimal' available/downloadable after sources.list rewrite+update

---

### Post by KegHead on 2011-04-28
Hi!

Wow!

what I would do is ;

[COLOR="Red"]Back up my docs, etc[/COLOR]

Do a fresh install of 11.04.

KegHead

---

### Post by penguin_brian on 2011-04-29
No need to panic.

I get that error because update-manager wrongly considers all my /etc/apt/sources.list entries to be 3rd party sources, and disables them. As such it cannot find the essential packages any more in the apt repositories. It looks like that is what is happening here too.

It does not mean anything is wrong with the computer, or that you need to consider a full reinstall.

How do I get update-manager to accept my sources? I want to use my local approx mirror, I shouldn't have use an official source.

Sometimes update-manager will ask me if I want to just blindly rewrite maverick everywhere to natty, but it seems very inconsistent. How do I force it to ask that question? It will work then.

Brian May

---

### Post by penguin_brian on 2011-04-30
I worked out what happened for me anyway. When upgrading my systems to 10.10, it automatically added the following line to my sources.list without me realizing:

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

When doing an upgrade, it decided that there was at least one official source, so wasn't going to let me do the rewrite step.

The work around was to comment out this line.

Brian May

---

