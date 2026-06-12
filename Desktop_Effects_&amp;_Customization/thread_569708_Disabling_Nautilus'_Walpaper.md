---
title: "Disabling Nautilus' Walpaper"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by mikeym on 2007-10-07
Hi,

I'm following the guide [here]("http://forum.compiz-fusion.org/showthread.php?p=30168#post30168") to stop nautilus from drawing my background wallpaper so that compiz can have a go at doing it (allowing a wallpaper for each side of the cube).

I downloaded the source for the 2 packages with:

```

sudo apt-get source nautilus
sudo apt-get source libeel2-2

```

Then I got the build dependencies for the 2 packages:

```

sudo apt-get build-dep nautilus
sudo apt-get build-dep libeel2-2

```

Then I downloaded the [2 patches]("http://bugzilla.gnome.org/show_bug.cgi?id=444320") from the guide. And saved *02_compiz_background.patch* to the eel folder (eel2-2.18.0.1) and *30_rgba_colormap.patch* to the nautilus folder (nautilus-2.18.1). 

Then I ran the 2 patches with:

```

cd nautilus-2.18.1
patch -p1 < 30_rgba_colormap.patch
cd ../eel2-2.18.0.1
patch -p1 < 02_compiz_background.patch

```

Then I tried to compile and install the debs with:

```

sudo apt-get -b source nautilus
sudo apt-get -b source libeel2-2
sudo dpkg -i nautilus_2.18.1-0ubuntu1_amd64.deb libnautilus-extension1_2.18.1-0ubuntu1_amd64.deb libeel2-2_2.18.0.1-0ubuntu1_amd64.deb libeel2-data_2.18.0.1-0ubuntu1_all.deb

```

Which all seemed to go OK but didn't produce any results. I checked the patches that were made by hand and they looked good. So there is probably something wrong with my approach - as I'm not used to compiling source using *apt*. 

Does anyone have any suggestions?

---

### Post by hyperair on 2007-10-07
Yeah. A simpler way, which doesn't affect all users. Just open up your gconf-editor, and change the value of /desktop/gnome/background/draw_background to false. Basically uncheck the checkbox. That should do the trick.

---

### Post by mikeym on 2007-10-07
That's strange. It doesn't seem to do anything at all. And I've reverted back to the repository nautilus.

---

### Post by mikeym on 2007-10-07
This must be why I get the error. I'm trying to compile using "*dpkg-buildpackage -rfakeroot -uc -b*" and I'm getting:

```

patches: debian/patches/01_lpi.patch debian/patches/02_autoconf.patch debian/patches/02_ubuntuspatial.patch debian/patches/03_menu_entry.patch debian/patches/05_defaultsettings.patch debian/patches/06_documents_place.patch debian/patches/07_gnomevfs_query_eject.patch debian/patches/08_display_mimetype_warning.patch debian/patches/10_rename_desktop.patch debian/patches/11_backup_files_list.patch debian/patches/80_suppress_umount_in_ltsp.patch debian/patches/81_gnome-app-install.patch debian/patches/93_upstream_nautilus-dnd-user-owned.patch
Trying patch debian/patches/01_lpi.patch at level 1 ... success.
Trying patch debian/patches/02_autoconf.patch at level 1 ... success.
Trying patch debian/patches/02_ubuntuspatial.patch at level 1 ... success.
Trying patch debian/patches/03_menu_entry.patch at level 1 ... 0 ... 2 ... failure.
make: *** [debian/stamp-patched] Error 1

```

I assume that this is because I have already patched *nautilus-2.19.2/src/nautilus-desktop-window.c* and then tried to build a package which causes more patches to be applied.

So how can I apply these patches to nautilus?

---

### Post by steveneddy on 2007-10-07
Seems like a simple question, but did you restart X?

Ctrl+Alt+Backspace

Just a thought.

:popcorn:

---

### Post by mikeym on 2007-10-07
Yes. After doing both - although it now looks like nautilus with the patch has never compiled properly. 

I have also tried setting */desktop/gnome/background/opacity* to 0 and various combinations of the two. 

So I'm still stuck wantong to know how to aply this patch.

---

### Post by hyperair on 2007-10-08
Strange, disabling nautilus's background from GConf worked for me. Have you tried disabling nautilus after that? Like killall nautilus, or restarting the X server.

---

### Post by mikeym on 2007-10-08
I have restarted the xserver, nautilus and the machine - disabling the background in gconf-editor does not work. (I have also tried every other combination of setting pictures drawing solids and levels of opacity none of which work to disable the background. Clicking */aps/nautilus/preferences/show_desktop* to *false* works instantly but does not show the desktop icons.). 

So does anyone know how to apply a patch to a source package that already has patches to be applied by the packager?

---

### Post by mikeym on 2007-10-08
Bump (sorry).

Perhaps this would have been better under packaging.

---

### Post by bb10 on 2007-10-15
I would also like to know how to get this working. Disabling draw_background is not a option because it also disables desktop icons.

---

### Post by mikeym on 2007-10-17
I have to admit that - unusualy for me - I have given up on this one. Suposedly there will be a patch like the one I was trying ot apply in Gusty.

---

### Post by plun on 2007-10-19
I haven't check which version source is now, it must be 2.20 or earlier
SVN was not possible to patch.

[http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/](http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/)
[http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/](http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/)

Unpack, patch and install,     ./configure , make, make install  as I  remembers it.

ccsm > enable wallpaper plugin

Syntax for wallpaper:
[B]
file:///home/plun/Desktop/Min/bilder/16.png:100[/B]

I switched to Debian Sid and also going to test it  :)  

All credits to "adamruss" in C-Fs forum...!

EDIT follow up

EEL must be compiled and installed.

Nautilus package must be removed... no icons and AWN on top, nautilus hangs a minute during start
[[img]http://pix.nofrag.com/7/e/2/b002e14d1edbc2d66fe619ffad778t.jpg[/img]](http://pix.nofrag.com/7/e/2/b002e14d1edbc2d66fe619ffad778.html)

Removed Nautilus package and installed from patched source...:)
X-restart

[[img]http://pix.nofrag.com/8/7/7/131205c7be47c6831a936e42e94d0t.jpg[/img]](http://pix.nofrag.com/8/7/7/131205c7be47c6831a936e42e94d0.html)

And.... this breaks a PC if a user doesnt know what he/she is doing...  Ctrl-Alt-F1 and tty is maybe important to know if Gnome crashes...:)

---

