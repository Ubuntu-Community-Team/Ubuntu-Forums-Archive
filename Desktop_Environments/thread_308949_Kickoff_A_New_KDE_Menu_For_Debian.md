---
title: "Kickoff A New KDE Menu For Debian?"
date: 2006-11-28
forum: Desktop Environments
---

### Post by raid517 on 2006-11-28
Hi I am trying to install Kickoff The KDE KMenu replacement in Kubuntu from SVN.  I managed to download everything OK and ./configure seemed to go fine - once I had installed all of the appropriate tools and libraries.

After running ./configure (which I ran with no additional options - as I was unsure of what options if any to use) I ran checkinstall to build a Debian based package and this seemed to get really quite far, right up to near the end of 'make install'.

However somewhere near what must be the end of the process (since it took a long time) I got the following error:

```
/usr/bin/install -c -p -m 644 'aurora.svgz.desktop' '/usr/share/wallpapers/aurora.svgz.desktop'
 /usr/bin/install -c -p -m 644 'celtic.svgz' '/usr/share/wallpapers/celtic.svgz'
 /usr/bin/install -c -p -m 644 'celtic.svgz.desktop' '/usr/share/wallpapers/celtic.svgz.desktop'
 /usr/bin/install -c -p -m 644 'globe.svgz' '/usr/share/wallpapers/globe.svgz'
 /usr/bin/install -c -p -m 644 'globe.svgz.desktop' '/usr/share/wallpapers/globe.svgz.desktop'
 /usr/bin/install -c -p -m 644 'here-gear.svgz' '/usr/share/wallpapers/here-gear.svgz'
 /usr/bin/install -c -p -m 644 'here-gear.svgz.desktop' '/usr/share/wallpapers/here-gear.svgz.desktop'
 /usr/bin/install -c -p -m 644 'konqui.svgz' '/usr/share/wallpapers/konqui.svgz'
 /usr/bin/install -c -p -m 644 'konqui.svgz.desktop' '/usr/share/wallpapers/konqui.svgz.desktop'
 /usr/bin/install -c -p -m 644 'lineart.svgz' '/usr/share/wallpapers/lineart.svgz'
 /usr/bin/install -c -p -m 644 'lineart.svgz.desktop' '/usr/share/wallpapers/lineart.svgz.desktop'
 /usr/bin/install -c -p -m 644 'moon.svgz' '/usr/share/wallpapers/moon.svgz'
 /usr/bin/install -c -p -m 644 'moon.svgz.desktop' '/usr/share/wallpapers/moon.svgz.desktop'
make[3]: Leaving directory `/home/raid517/suse_kickoff/pics/wallpapers'
make[2]: Leaving directory `/home/raid517/suse_kickoff/pics/wallpapers'
make[2]: Entering directory `/home/raid517/suse_kickoff/pics'
make[3]: Entering directory `/home/raid517/suse_kickoff/pics'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/raid517/suse_kickoff/pics'
make[2]: Leaving directory `/home/raid517/suse_kickoff/pics'
make[1]: Leaving directory `/home/raid517/suse_kickoff/pics'
Making install in konqueror
make[1]: Entering directory `/home/raid517/suse_kickoff/konqueror'
Making install in .
make[2]: Entering directory `/home/raid517/suse_kickoff/konqueror'
make[3]: Entering directory `/home/raid517/suse_kickoff/konqueror'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  'libkdeinit_konqueror.la' '/usr/lib/libkdeinit_konqueror.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  'konqueror' '/usr/bin/konqueror'
/bin/sh ../admin/mkinstalldirs /usr/share/apps/konqueror/profiles
/usr/bin/install -c -p -m 644 ./profile_webbrowsing.desktop /usr/share/apps/konqueror/profiles/webbrowsing
/usr/bin/install -c -p -m 644 ./profile_filemanagement.desktop /usr/share/apps/konqueror/profiles/filemanagement
/usr/bin/install -c -p -m 644 ./profile_midnightcommander.desktop /usr/share/apps/konqueror/profiles/midnightcommander
/usr/bin/install -c -p -m 644 ./profile_tabbedbrowsing.desktop /usr/share/apps/konqueror/profiles/tabbedbrowsing
/usr/bin/install -c -p -m 644 ./profile_kde_devel.desktop /usr/share/apps/konqueror/profiles/kde_devel
/usr/bin/install -c -p -m 644 ./profile_simplebrowser.desktop /usr/share/apps/konqueror/profiles/simplebrowser
test -z "/usr/include" || mkdir -p -- "/usr/include"
 /usr/bin/install -c -p -m 644 'KonquerorIface.h' '/usr/include/KonquerorIface.h'
test -z "/usr/share/applnk" || mkdir -p -- "/usr/share/applnk"
 /usr/bin/install -c -p -m 644 'konqueror.desktop' '/usr/share/applnk/konqueror.desktop'
test -z "/usr/share/config.kcfg" || mkdir -p -- "/usr/share/config.kcfg"
 /usr/bin/install -c -p -m 644 'konqueror.kcfg' '/usr/share/config.kcfg/konqueror.kcfg'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  'konqueror.la' '/usr/lib/kde3/konqueror.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
test -z "/usr/share/applnk/.hidden" || mkdir -p -- "/usr/share/applnk/.hidden"
 /usr/bin/install -c -p -m 644 'konqfilemgr.desktop' '/usr/share/applnk/.hidden/konqfilemgr.desktop'
test -z "/usr/share/apps/konqueror" || mkdir -p -- "/usr/share/apps/konqueror"
 /usr/bin/install -c -p -m 644 'konqueror.rc' '/usr/share/apps/konqueror/konqueror.rc'
 /usr/bin/install -c -p -m 644 'konq-simplebrowser.rc' '/usr/share/apps/konqueror/konq-simplebrowser.rc'
test -z "/usr/share/applications/kde" || mkdir -p -- "/usr/share/applications/kde"
 /usr/bin/install -c -p -m 644 'kfmclient.desktop' '/usr/share/applications/kde/kfmclient.desktop'
 /usr/bin/install -c -p -m 644 'kfmclient_dir.desktop' '/usr/share/applications/kde/kfmclient_dir.desktop'
 /usr/bin/install -c -p -m 644 'kfmclient_html.desktop' '/usr/share/applications/kde/kfmclient_html.desktop'
 /usr/bin/install -c -p -m 644 'kfmclient_war.desktop' '/usr/share/applications/kde/kfmclient_war.desktop'
 /usr/bin/install -c -p -m 644 'konqbrowser.desktop' '/usr/share/applications/kde/konqbrowser.desktop'
 /usr/bin/install -c -p -m 644 'konquerorsu.desktop' '/usr/share/applications/kde/konquerorsu.desktop'
 /usr/bin/install -c -p -m 644 'Home.desktop' '/usr/share/applications/kde/Home.desktop'
make[3]: Leaving directory `/home/raid517/suse_kickoff/konqueror'
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror'
Making install in client
make[2]: Entering directory `/home/raid517/suse_kickoff/konqueror/client'
make[3]: Entering directory `/home/raid517/suse_kickoff/konqueror/client'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'libkdeinit_kfmclient.la' '/usr/lib/libkdeinit_kfmclient.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'kfmclient' '/usr/bin/kfmclient'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'kfmclient.la' '/usr/lib/kde3/kfmclient.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
test -z "/usr/share/apps/kconf_update" || mkdir -p -- "/usr/share/apps/kconf_update"
 /usr/bin/install -c -p -m 644 'kfmclient_3_2.upd' '/usr/share/apps/kconf_update/kfmclient_3_2.upd'
test -z "/usr/share/apps/kconf_update" || mkdir -p -- "/usr/share/apps/kconf_update"
 /usr/bin/install -c -p 'kfmclient_3_2_update.sh' '/usr/share/apps/kconf_update/kfmclient_3_2_update.sh'
make[3]: Leaving directory `/home/raid517/suse_kickoff/konqueror/client'
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror/client'
Making install in iconview
make[2]: Entering directory `/home/raid517/suse_kickoff/konqueror/iconview'
make[3]: Entering directory `/home/raid517/suse_kickoff/konqueror/iconview'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'konq_iconview.la' '/usr/lib/kde3/konq_iconview.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
test -z "/usr/share/services" || mkdir -p -- "/usr/share/services"
 /usr/bin/install -c -p -m 644 'konq_iconview.desktop' '/usr/share/services/konq_iconview.desktop'
 /usr/bin/install -c -p -m 644 'konq_multicolumnview.desktop' '/usr/share/services/konq_multicolumnview.desktop'
test -z "/usr/share/apps/konqiconview" || mkdir -p -- "/usr/share/apps/konqiconview"
 /usr/bin/install -c -p -m 644 'konq_iconview.rc' '/usr/share/apps/konqiconview/konq_iconview.rc'
 /usr/bin/install -c -p -m 644 'konq_multicolumnview.rc' '/usr/share/apps/konqiconview/konq_multicolumnview.rc'
make[3]: Leaving directory `/home/raid517/suse_kickoff/konqueror/iconview'
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror/iconview'
Making install in listview
make[2]: Entering directory `/home/raid517/suse_kickoff/konqueror/listview'
make[3]: Entering directory `/home/raid517/suse_kickoff/konqueror/listview'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'konq_listview.la' '/usr/lib/kde3/konq_listview.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
test -z "/usr/share/config.kcfg" || mkdir -p -- "/usr/share/config.kcfg"
 /usr/bin/install -c -p -m 644 'konq_listview.kcfg' '/usr/share/config.kcfg/konq_listview.kcfg'
test -z "/usr/share/services" || mkdir -p -- "/usr/share/services"
 /usr/bin/install -c -p -m 644 'konq_treeview.desktop' '/usr/share/services/konq_treeview.desktop'
 /usr/bin/install -c -p -m 644 'konq_detailedlistview.desktop' '/usr/share/services/konq_detailedlistview.desktop'
 /usr/bin/install -c -p -m 644 'konq_textview.desktop' '/usr/share/services/konq_textview.desktop'
 /usr/bin/install -c -p -m 644 'konq_infolistview.desktop' '/usr/share/services/konq_infolistview.desktop'
test -z "/usr/share/apps/konqlistview" || mkdir -p -- "/usr/share/apps/konqlistview"
 /usr/bin/install -c -p -m 644 'konq_treeview.rc' '/usr/share/apps/konqlistview/konq_treeview.rc'
 /usr/bin/install -c -p -m 644 'konq_detailedlistview.rc' '/usr/share/apps/konqlistview/konq_detailedlistview.rc'
 /usr/bin/install -c -p -m 644 'konq_textview.rc' '/usr/share/apps/konqlistview/konq_textview.rc'
 /usr/bin/install -c -p -m 644 'konq_infolistview.rc' '/usr/share/apps/konqlistview/konq_infolistview.rc'
make[3]: Leaving directory `/home/raid517/suse_kickoff/konqueror/listview'
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror/listview'
Making install in keditbookmarks
make[2]: Entering directory `/home/raid517/suse_kickoff/konqueror/keditbookmarks'
make[2]: *** No rule to make target `/usr/include/kbookmarknotifier.h', needed by `kbookmarknotifier.kidl'.  Stop.
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror/keditbookmarks'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/raid517/suse_kickoff/konqueror'
make: *** [install-recursive] Error 1
```Throughout the build process I get a reoccurring error too, from rm (or remove) saying "rm cannot remove is a directory" so it seems that the build script has some problems with removing items after building them - although I am uncertain if this is fatal.

Can anyone possibly suggest a way to resolve this?

P.S.

You can see Kickoff in action here:

[http://home.kde.org/~binner/kickoff/sneak_preview.html](http://home.kde.org/~binner/kickoff/sneak_preview.html)

---

