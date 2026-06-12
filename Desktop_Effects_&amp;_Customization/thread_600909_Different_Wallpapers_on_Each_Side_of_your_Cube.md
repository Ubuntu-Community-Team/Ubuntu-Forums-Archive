---
title: "Different Wallpapers on Each Side of your Cube"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by klange on 2007-11-02
***[color=red]Snap! This script is OUTDATED, FAULTY, and HORRIBLY POINTLESS![/color]***
I've removed the script to ensure that no one ever uses it again.
Want multiple wallpapers with icons? Use Kubuntu 8.04 or Ubuntu 8.04 with some Launcher screenlets.

---

### Post by pt123 on 2007-11-02
Thank you very much for this. 
This wallpaper limitation has been so frustrating. 

I am not sure how the gnome devs. never understood that a different wallpaper is the easiest way for a user to differentiate the desktops. 

Also is there a way to install just the wallpaper plugin if you already have compiz 0.62 installed?

---

### Post by klange on 2007-11-02
> **pt123 said:**
> Also is there a way to install just the wallpaper plugin if you already have compiz 0.62 installed?
Unfortunately, no, I haven't been able to find one that compiles with the Gutsy (or Feisty, for that matter) installation of Compiz. You may be able to look back in the git to find an older version of the plugin that will compile, but I didn't have any luck.
If you or someone else does happen to find one that compiles, I can change the script to install that instead. It would save a lot of time (I just reran this today on my laptop to ensure it worked, took around 10 minutes).
EDIT: Also, if you do run this, let me know if you still have "Create Archive" / "Extract Here" as options when you right click a file / archive (when you have it working). I need to make sure that reinstalling file-roller works, I can't tell because I can't even tell if it reinstalled (I built from the latest stable and then tried reinstalling, and it still seams that that's the one I have [2.18.4]). If you don't, do as I did and compile from source, but let me know as well.

---

### Post by pt123 on 2007-11-02
I was thinking,since  I could get different WPs to appear through compiz by disabling the show-desktop option in Nautilus (but I lose Icons on the desktop) so it possible to just patch Nautilus without re-installing & recompiling Compiz, to get the different WPs to work?

---

### Post by klange on 2007-11-02
If your wallpaper plugin works right now, just patch up Nautilus.
```
echo -e "Downloading libeel 2.20 source...           \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Downloading Nautilus 2.20 source...         \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Building libeel...                          \c"
tar jxvf eel-2.20.0.tar.bz2 1>/dev/null
cd eel-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/eel.patch 2>/dev/null
patch -p1 < eel.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Nautilus...                        \c"
tar jxvf nautilus-2.20.0.tar.bz2 1>/dev/null
cd nautilus-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/nautilus.patch 2>/dev/null
patch -p1 < nautilus.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Reinstalling file-roller...                 \c"
sudo aptitude reinstall file-roller 1>/dev/null
echo "[ DONE ]"
```

---

### Post by pt123 on 2007-11-02
> **WindowsSucks said:**
> If your wallpaper plugin works right now, just patch up Nautilus.

Well it is achieved through the Desktop Cube -> Appearance -> Background images setting.
There is no WP plugin installed on my Compiz.

---

### Post by klange on 2007-11-02
Hmm, I didn't know about that built-in functionality. Though I might add I'm not sure if it'll work directly as an environment variable has to be set, and I believe only the wallpaper plugin sets it (You can set it manually, I don't remember what it is...)

---

### Post by New2Ubunt2 on 2007-11-03
Hi There :)

Had a little trouble with this. Per your instructions, you say to remove compiz. It seems to me that in order to make a backup of /usr/bin/compiz, it has to be installed, but your instructions call for it to be removed ahead of time. When I remove compiz, user/bin/compiz disappears and the script does not work. I was able to manually back it up and run the script, but I get the following errors:

```
Building Compiz 0.6.2...                     In file included from decorator.moc.cpp:11:
decorator.h:27:26: error: kapplication.h: No such file or directory
decorator.h:35:21: error: fixx11h.h: No such file or directory
decorator.h:36:21: error: kconfig.h: No such file or directory
decorator.h:37:35: error: kdecoration_plugins_p.h: No such file or directory
decorator.h:38:27: error: kdecoration_p.h: No such file or directory
decorator.h:39:19: error: netwm.h: No such file or directory
decorator.h:44:29: error: dbus/connection.h: No such file or directory
In file included from window.h:37,
                 from decorator.h:46,
                 from decorator.moc.cpp:11:
options.h:27:25: error: kdecoration.h: No such file or directory
In file included from decorator.h:47,
                 from decorator.moc.cpp:11:
KWinInterface.h:6:24: error: dcopobject.h: No such file or directory
/usr/share/qt3/include/qnamespace.h:838: error: expected identifier before numeric constant
/usr/share/qt3/include/qnamespace.h:838: error: expected unqualified-id before numeric constant
/usr/share/qt3/include/qevent.h:61: error: expected identifier before numeric constant
/usr/share/qt3/include/qevent.h:61: error: expected `}' before numeric constant
/usr/share/qt3/include/qevent.h:61: error: expected unqualified-id before numeric constant
/usr/share/qt3/include/qevent.h:142: error: expected `)' before &#8216;type&#8217;
/usr/share/qt3/include/qevent.h:143: error: declaration of &#8216;~QEvent&#8217; as non-member
/usr/share/qt3/include/qevent.h:144: error: &#8216;Type&#8217; does not name a type
/usr/share/qt3/include/qevent.h:145: error: non-member function &#8216;bool spontaneous()&#8217; cannot have cv-qualifier
/usr/share/qt3/include/qevent.h: In function &#8216;bool spontaneous()&#8217;:
/usr/share/qt3/include/qevent.h:145: error: &#8216;spont&#8217; was not declared in this scope
/usr/share/qt3/include/qevent.h: At global scope:
/usr/share/qt3/include/qevent.h:146: error: expected unqualified-id before &#8216;protected&#8217;
/usr/share/qt3/include/qevent.h:148: error: expected unqualified-id before &#8216;private&#8217;
/usr/share/qt3/include/qevent.h:150: error: invalid function declaration
/usr/share/qt3/include/qevent.h:153: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:154: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:155: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:156: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:157: error: expected declaration before &#8216;}&#8217; token
make[3]: *** [decorator.moc.o] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
libtool: install: warning: relinking `libdecoration.la'
libtool: install: warning: relinking `libblur.la'
libtool: install: warning: relinking `libvideo.la'
libtool: install: warning: relinking `libsvg.la'
In file included from decorator.moc.cpp:11:
decorator.h:27:26: error: kapplication.h: No such file or directory
decorator.h:35:21: error: fixx11h.h: No such file or directory
decorator.h:36:21: error: kconfig.h: No such file or directory
decorator.h:37:35: error: kdecoration_plugins_p.h: No such file or directory
decorator.h:38:27: error: kdecoration_p.h: No such file or directory
decorator.h:39:19: error: netwm.h: No such file or directory
decorator.h:44:29: error: dbus/connection.h: No such file or directory
In file included from window.h:37,
                 from decorator.h:46,
                 from decorator.moc.cpp:11:
options.h:27:25: error: kdecoration.h: No such file or directory
In file included from decorator.h:47,
                 from decorator.moc.cpp:11:
KWinInterface.h:6:24: error: dcopobject.h: No such file or directory
/usr/share/qt3/include/qnamespace.h:838: error: expected identifier before numeric constant
/usr/share/qt3/include/qnamespace.h:838: error: expected unqualified-id before numeric constant
/usr/share/qt3/include/qevent.h:61: error: expected identifier before numeric constant
/usr/share/qt3/include/qevent.h:61: error: expected `}' before numeric constant
/usr/share/qt3/include/qevent.h:61: error: expected unqualified-id before numeric constant
/usr/share/qt3/include/qevent.h:142: error: expected `)' before &#8216;type&#8217;
/usr/share/qt3/include/qevent.h:143: error: declaration of &#8216;~QEvent&#8217; as non-member
/usr/share/qt3/include/qevent.h:144: error: &#8216;Type&#8217; does not name a type
/usr/share/qt3/include/qevent.h:145: error: non-member function &#8216;bool spontaneous()&#8217; cannot have cv-qualifier
/usr/share/qt3/include/qevent.h: In function &#8216;bool spontaneous()&#8217;:
/usr/share/qt3/include/qevent.h:145: error: &#8216;spont&#8217; was not declared in this scope
/usr/share/qt3/include/qevent.h: At global scope:
/usr/share/qt3/include/qevent.h:146: error: expected unqualified-id before &#8216;protected&#8217;
/usr/share/qt3/include/qevent.h:148: error: expected unqualified-id before &#8216;private&#8217;
/usr/share/qt3/include/qevent.h:150: error: invalid function declaration
/usr/share/qt3/include/qevent.h:153: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:154: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:155: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:156: error: &#8216;friend&#8217; can only be specified inside a class
/usr/share/qt3/include/qevent.h:157: error: expected declaration before &#8216;}&#8217; token
make[2]: *** [decorator.moc.o] Error 1
make[1]: *** [install-recursive] Error 1
make: *** [install-recursive] Error 1

```

Any ideas on what I did wrong?

Edit:Are you using Gnome or KDE?

---

### Post by pt123 on 2007-11-03
when I tried the script it crashed on building libeel

```

Alternatively, you may set the environment variables EEL_CFLAGS
and EEL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
[ DONE ]
-e Building Nautilus...                        configure: error: Package requirements (
        esound                  >= 0.2.27
        bonobo-activation-2.0   >= 2.1.0
        eel-2.0                 >= 2.15.91
        glib-2.0                >= 2.6.0
        gnome-desktop-2.0       >= 2.9.91
        gnome-vfs-2.0           >= 2.19.3
        gnome-vfs-module-2.0    >= 2.19.3
        ORBit-2.0               >= 2.4.0
        pango                   >= 1.1.2
        gtk+-2.0                >= 2.11.6
        libart-2.0              >= 2.3.10
        libbonobo-2.0           >= 2.1.0
        libgnome-2.0            >= 2.14.0
        libgnomeui-2.0          >= 2.6.0
        librsvg-2.0             >= 2.0.1
        libxml-2.0              >= 2.4.7
        libstartup-notification-1.0
) were not met:

No package 'eel-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALL_CFLAGS
and ALL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

One of the reasons I hate compiling software there is always a problem with  PKG_CONFIG_PATH 
it is rarely simple as :

$ ./configure
$ make
$ make install
:)

---

### Post by meindian523 on 2007-11-03
I downloaded the script,made it executable and ran it.This is what I got.
```
root@l1nuxr0cks:~# ./patchfordiffwallpapers.sh 
Downloading libeel 2.20 source...           [ DONE ]
Downloading Nautilus 2.20 source...         [ DONE ]
Building libeel...                          configure: error: Package requirements (
        gail                    >= 0.16
        gconf-2.0               >= 1.1.11
        gdk-pixbuf-2.0          >= 2
        glib-2.0                >= 2.6.0
        gnome-vfs-2.0           >= 2.9.1
        gnome-vfs-module-2.0    >= 2.9.1
        gthread-2.0             >= 2.6.0
        gtk+-2.0                >= 2.9.4
        libart-2.0              >= 2.3.8
        libglade-2.0            >= 2.0.0
        libgnome-2.0            >= 2.0
        libgnomeui-2.0          >= 2.7.92
        libxml-2.0              >= 2.4.7
        libgnome-menu           >= 2.13.5
        gnome-desktop-2.0       >= 2.1.4
) were not met:

No package 'gail' found
No package 'gconf-2.0' found
No package 'gdk-pixbuf-2.0' found
No package 'glib-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'gthread-2.0' found
No package 'gtk+-2.0' found
No package 'libart-2.0' found
No package 'libglade-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found
No package 'libgnome-menu' found
No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EEL_CFLAGS
and EEL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
[ DONE ]
Building Nautilus...                        configure: error: Package requirements (
        esound                  >= 0.2.27
        bonobo-activation-2.0   >= 2.1.0
        eel-2.0                 >= 2.15.91
        glib-2.0                >= 2.6.0
        gnome-desktop-2.0       >= 2.9.91
        gnome-vfs-2.0           >= 2.19.3
        gnome-vfs-module-2.0    >= 2.19.3
        ORBit-2.0               >= 2.4.0
        pango                   >= 1.1.2
        gtk+-2.0                >= 2.11.6
        libart-2.0              >= 2.3.10
        libbonobo-2.0           >= 2.1.0
        libgnome-2.0            >= 2.14.0
        libgnomeui-2.0          >= 2.6.0
        librsvg-2.0             >= 2.0.1
        libxml-2.0              >= 2.4.7

) were not met:

No package 'esound' found
No package 'bonobo-activation-2.0' found
No package 'eel-2.0' found
No package 'glib-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'ORBit-2.0' found
No package 'pango' found
No package 'gtk+-2.0' found
No package 'libart-2.0' found
No package 'libbonobo-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'librsvg-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALL_CFLAGS
and ALL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
[ DONE ]
Reinstalling file-roller...                 [ DONE ]
root@l1nuxr0cks:~#
```

---

### Post by meindian523 on 2007-11-03
> **WindowsSucks said:**
> If your wallpaper plugin works right now, just patch up Nautilus.
```
echo -e "Downloading libeel 2.20 source...           \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Downloading Nautilus 2.20 source...         \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Building libeel...                          \c"
tar jxvf eel-2.20.0.tar.bz2 1>/dev/null
cd eel-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/eel.patch 2>/dev/null
patch -p1 < eel.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Nautilus...                        \c"
tar jxvf nautilus-2.20.0.tar.bz2 1>/dev/null
cd nautilus-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/nautilus.patch 2>/dev/null
patch -p1 < nautilus.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Reinstalling file-roller...                 \c"
sudo aptitude reinstall file-roller 1>/dev/null
echo "[ DONE ]"
```

I used this one since tho' my C-F is 0.5.1,my wallpaper plugin works.

---

### Post by pt123 on 2007-11-03
Is it possible to get deb of the libeel, why does it require so many packages to build.

---

### Post by klange on 2007-11-03
You should already have Libeel.
Try
```
sudo apt-get build-dep nautilus
```

---

### Post by meindian523 on 2007-11-03
I guess I will let this luxury pass because not only has my WP plugin conked out,my cube rotate has slowed down to a crawl........:(

---

### Post by klange on 2007-11-03
If you're having problems and really want to get this working, you can hit me up on:
MSN: admiralbacon AT gmail DOT com
AIM: OasisGamesCom
My Forum: [http://home.oasis-games.com](http://home.oasis-games.com)

---

### Post by Jose Catre-Vandis on 2007-11-03
> **pt123 said:**
> I was thinking,since  I could get different WPs to appear through compiz by disabling the show-desktop option in Nautilus (but I lose Icons on the desktop) so it possible to just patch Nautilus without re-installing & recompiling Compiz, to get the different WPs to work?

This works a treat, if you don't mind not having icons on your desktops.

```
sudo gconf-editor
```
apps>nautilus>preferences and untick "show desktop"
shut gconf-editor

Open up ccsm and click on Desktop Cube to open up the options, and select the Behaviour tab

Under Background Images, click the +Add button and start adding wallpaper on at a time for all the sides of your cube. Check they are in the right places by activating the cube, if not use the Up and Down buttons to move them about.

Save out and you have a wallpaper for each side of your cube - hogging memory :) :lol:

---

### Post by forestpixie on 2007-11-03
> **Jose Catre-Vandis said:**
> This works a treat, if you don't mind not having icons on your desktops.

```
sudo gconf-editor
```
apps>nautilus>preferences and untick "show desktop"
shut gconf-editor

Open up ccsm and click on Desktop Cube to open up the options, and select the Behaviour tab

Under Background Images, click the +Add button and start adding wallpaper on at a time for all the sides of your cube. Check they are in the right places by activating the cube, if not use the Up and Down buttons to move them about.

Save out and you have a wallpaper for each side of your cube - hogging memory :) :lol:

I did this - and then changed my mind ;)

so I undid it all and now I can't get icons back on my desktop, right clicking on the desktop doesn't get a menu - it's all gone :( - anyone know what I need to do to get it back 

TIA

---

### Post by klange on 2007-11-03
Open a terminal and start nautilus manually.

Again, if you have the wallpaper plugin working, just patch up nautilus so that it runs with a transparent background, giving you your icons and your wallpapers. If the plugin ever gives you problems, simply reinstall Nautilus with Synaptic.

---

### Post by forestpixie on 2007-11-03
how do you restart nautilus? if you mean just typing nautilus and then entering , runs an instance of nautilus but doesn't do anything about the desktop icons. The wallpaper is working fine - it's the icons which seem to have gone awol. It won't either let me drag then to the desktop.

And the window border has changed colour as well - changing themes or customising them doesn't make any difference to the awful purple colour :(

Edit  - also my windows title border should be in italics - but that's not either.

---

### Post by pt123 on 2007-11-03
a screenshot might be a good idea

---

### Post by klange on 2007-11-03
1. Ensure that your Nautilus settings are actually set for drawing the desktop.
2. Again, restart Nautilus.
3. Try restarting your computer, or at the very least logging out and then back in.
4. Your window title bar problem is a problem with Emerald, and nothing I or any one else has mentioned should mess with that. Also, Emerald uses a file to start its configuration, check to make sure the file (which is under /home/[user]/.emerald/theme) has the right settings in it and restart Emerald.

---

### Post by forestpixie on 2007-11-03
wouldn't know how to do 1 - so it'd be handy to know for next time :)

- I'd forgotten about emerald - had installed it earlier but not done anything with it - so I uninstalled it before I restarted - restarting sorted it out

just got to wait for the menu dropdown to be sorted out and I'll be a happy bunny

Thanks

---

### Post by pt123 on 2007-11-03
for 1 just read a few pages back my post and Jose Catre-Vandis

---

### Post by Rinzwind on 2007-11-03
Looks very cool but I want to keep my backgrounds to change every x minutes. 

Do you think with these changes a compiz dev would hack in a slider with a timer? :D

---

### Post by klange on 2007-11-03
You could write a script that changes the configuration value for the wallpapers plugin, giving you multiple wallpapers that change periodically. That would be interesting...

As for "number 1", you need to use gconf-editor to make sure that the Nautilus is set to draw the desktop. It's under /apps/nautilus/preferences -> show_desktop 

You need to make sure you do that if you're currently using the Wallpaper plugin without this patch as well.

---

### Post by forestpixie on 2007-11-03
> **WindowsSucks said:**
> As for "number 1", you need to use gconf-editor to make sure that the Nautilus is set to draw the desktop. It's under /apps/nautilus/preferences -> show_desktop 

aah - I'd done that, can't remember if I restarted after I  did it though :)

---

### Post by Rinzwind on 2007-11-03
> **WindowsSucks said:**
> You could write a script that changes the configuration value for the wallpapers plugin, giving you multiple wallpapers that change periodically. That would be interesting...


I've been thinking about that too :)

But I think it's better to approach this from another way:

I made my own desktop changer a while back (just for fun) that uses:

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$WallpapersDir$RandomDir$RandomPix 
gconftool-2 -t str --set /apps/gnome-session/options/splash_image "$WallpapersDir$RandomDir$RandomPix"

If I could find how to edit the compiz plugin and change those wallpapers I'd be there,
Plus it could be rather cool: have it check for compiz plugin and change that or otherwise change gconftool (if plugin not active) . But I don't know if it's possible and where to start :)

Currently I use wallpaper-tray (cuz I didn't feel like making a GUI YET ;) ) 

Biggest advantage: the normal wallpaperchanger (like wallpaper-tray and/or desktop drapes) would still be funtional :)

Hmmm I'm interested. And when I am interested I start searching :+ Maybe I can find how to do this.

---

### Post by pt123 on 2007-11-03
Here is a script I made to change WPs,
[http://ubuntuforums.org/showpost.php?p=2816683&postcount=24](http://ubuntuforums.org/showpost.php?p=2816683&postcount=24)

If you change compiz to use gconf as its back end you can modify this.

---

### Post by klange on 2007-11-03
The wallpaper plugin uses a list where each element is in the following format:
file:[path to file]:100
'file' is the type of image to use, since we want files, we put 'file'
'100' is the opacity. I'm not sure how it works with anything less (I believe it uses the Gnome background and draws over it)

---

### Post by Rinzwind on 2007-11-04
> **WindowsSucks said:**
> The wallpaper plugin uses a list where each element is in the following format:
file:[path to file]:100
'file' is the type of image to use, since we want files, we put 'file'
'100' is the opacity. I'm not sure how it works with anything less (I believe it uses the Gnome background and draws over it)

hmmm wallpaper plugin is your plugin? or is that a plugin used inside the cube plugin?

I can find my backgrounds in:
~/.gconf/apps/compiz/plugins/cube/screen0/options

 more %gconf.xml 
<?xml version="1.0"?>
<gconf>
        <entry name="backgrounds" mtime="1194160979" type="list" ltype="string">
                <li type="string">
                        <stringvalue>/home/{username}/Pictures/folklore4.jpg</stringvalue>
                </li>
<..>
        </entry>
        <entry name="multioutput_mode" mtime="1194160979" type="int" value="1">
        </entry>
</gconf>

See? But this one is generated it seems (change the file and open ccsm and the file is back to the original). :)

---

### Post by klange on 2007-11-04
The Wallpaper plugin was added in 0.6.0 as a replacement to using the cube background tool (as well as allowing the same effect for the Wall plugin).
It also gives a few extra features and is more stable than the cube background.

Having a different wallpaper on each side without icons has been around for a while, but this patch for Nautilus (see page 1) is the key to a true multiple-wallpaper "desktop" - it draws a transparent wallpaper so your icons are there and work (and so does the right click menu), but it allows the Wallpaper plugin for C-F to draw your wallpapers, giving the effect we've all been looking for for quite a while.

Also, that's a gconf file. Open up gconf-editor and find that same path (/apps/compiz/plugins/cube/screen0/options), and you'll have that same information. I had no idea such a functionality existed, I just know that the wallpaper plugin works *better*.

---

### Post by quadm on 2007-11-04
Thanks a lot for the How-To. Im installing it now....

Any chance of you writing one on installing freewins? that would be much appreciated. I've searched everywhere i cant find one.

---

### Post by averagebeatboy on 2007-11-04
Hi,

I love the feature of different wallpapers on the cube. Thank you for your time, trouble and work on it.  I was wondering, I have never used the Cube [I know I just performed sacrilege ... laughing].

But a user bought up a GREAT POINT.  I do not even use the 2 different windows to unclutter the first window when I am working on a project and I think the user hit the proverbial nail on the head when he said something to the effect that it is hard to differentiate the two screens without a different background on screen 1 and screen 2.


Do you think this plugin would work on just the two plain surfaces allowing me to differentiate my screens as I go back and forth rather than trying to reach untold buried windows I have opened and need to remain opened for, or until, my project is finished?

Thanks in advance for any assistance or answer.

Cheers,

Averagebeatboy

---

### Post by Rinzwind on 2007-11-05
Me too. I love the idea. But I love the idea of random wallpapers more :D :D

---

### Post by Rinzwind on 2007-11-06
Turn show_desktop off so Compiz gets control:

gconftool-2 --type bool --list-type=bool --set /apps/nautilus/preferences/show_desktop false

Change the pictures set inside plugin 'cube':

gconftool-2 --type list --list-type=string --set /apps/compiz/plugins/cube/screen0/options/backgrounds [/files/Pictures/xxxHolic_01.jpg,/files/Pictures/xxxHolic_02.jpg,/files/Pictures/xxxHolic_03.jpg,/files/Pictures/xxxHolic_04.jpg]

When changed it works like a charm :D :D
I used above script and added this line and hardcoded 2 sets with 4 different pictures :)

BTW: if I turn show_desktop to FALSE it becomes very sluggish. Plus setting it back to TRUE does not seem to work unless I relog.

---

### Post by ghettowarrior on 2007-11-09
does anyone know what is wrong with the gtk+ 2.0 
i cant get nautilus compiled because of the gtk_widget_set_colormap bug

---

### Post by nikoPSK on 2007-11-12
k Im in gutsy with default compiz and the dettings manager. is there any way to do this without installing 0.6.0. of compiz?

---

### Post by 469tc on 2007-11-12
> **WindowsSucks said:**
> A couple of people have asked me how I did it, and the answer is simply "there was a tutorial", but that tutorial (link *was* in my sig) is a pretty bleak thing for some Ubuntu users who have no idea where to begin, so here I am writing a better one, tuned specifically to Ubuntu.
[[img]http://images.ogunderground.com/gal/Halo_3/_thb_cube_full.png[/img][img]http://images.ogunderground.com/gal/Halo_3/_thb_cube_full_b.png[/img]](http://images.ogunderground.com/index.php?spgmGal=Halo_3)
The following bash script will download and install Compiz 0.6.2, with the wallpaper plugin, get the source for Nautilus 2.2 and eel, apply the patches, compile both, and maintain the standard Ubuntu Compiz starter script. It shouldn't print anything other than the status lines unless there are errors.
**EDIT**: WARNING! Be sure to _remove_ Compiz before running this script or things can get messy!
*Note: I only tested this once on my laptop, which already had everything. If you have any problems, let me know.*
```
#!/bin/bash
#       "blah blah blah blah                          \c"
# echo "[ DONE ]"                                      
echo -e "Backing up Compiz execution script...        \c"
sudo mv /usr/bin/compiz /usr/bin/compiz_TEMP  1>/dev/null
echo "[ DONE ]"
echo -e "Installing prerequisites...                  \c"
sudo apt-get install build-essential gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev python-dev python-pyrex 1>/dev/null
echo "[ DONE ]"
echo -e "Downloading tarbells...                      \c"
wget -r -np -nd --accept=tar.bz2 http://releases.compiz-fusion.org/0.6.0/ 2>/dev/null
echo "[ DONE ]"
echo -e "Building Compiz 0.6.2...                     \c"
tar jxvf compiz-0.6.2.tar.bz2 1>/dev/null
cd compiz-0.6.2/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Compiz Bcop...                      \c"
tar jxvf compiz-bcop-0.6.0.tar.bz2 1>/dev/null
cd compiz-bcop-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building libcompizconfig...                  \c"
tar jxvf libcompizconfig-0.6.0.tar.bz2 1>/dev/null
cd libcompizconfig-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compizconfig-python...              \c"
tar jxvf compizconfig-python-0.6.0.tar.bz2 1>/dev/null
cd compizconfig-python-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building ccsm...                             \c"
tar jxvf ccsm-0.6.0.tar.bz2 1>/dev/null
cd ccsm-0.6.0/
sudo python setup.py install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compiz-fusion-plugins-main...       \c"
tar jxvf compiz-fusion-plugins-main-0.6.0.tar.bz2 1>/dev/null
cd compiz-fusion-plugins-main-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compuz-fusion-plugins-extra...      \c"
tar jxvf compiz-fusion-plugins-extra-0.6.0.tar.bz2 1>/dev/null
cd compiz-fusion-plugins-extra-0.6.0/
./configure --prefix=/usr 1>/dev/null
sudo make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building -plugins-unsupported...             \c"
tar jxvf compiz-fusion-plugins-unsupported-0.6.0.tar.bz2 1>/dev/null
cd compiz-fusion-plugins-unsupported-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compizconfig-backend-gconf...       \c"
tar jxvf compizconfig-backend-gconf-0.6.0.tar.bz2 1>/dev/null
cd compizconfig-backend-gconf-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Restoring compiz starter...                 \c"
sudo mv /usr/bin/compiz /usr/bin/compiz.real 1>/dev/null
sudo mv /usr/bin/compiz_TEMP /usr/bin/compiz 1>/dev/null
echo "[ DONE ]"
echo -e "Downloading libeel 2.20 source...           \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Downloading Nautilus 2.20 source...         \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Building libeel...                          \c"
tar jxvf eel-2.20.0.tar.bz2 1>/dev/null
cd eel-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/eel.patch 2>/dev/null
patch -p1 < eel.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Nautilus...                        \c"
tar jxvf nautilus-2.20.0.tar.bz2 1>/dev/null
cd nautilus-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/nautilus.patch 2>/dev/null
patch -p1 < nautilus.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Reinstalling file-roller...                 \c"
sudo aptitude reinstall file-roller 1>/dev/null
echo "[ DONE ]"

```

After that, just restart (to ensure that everything is running properly), open up CCSM, enable the Wallpaper plugin and add your wallpapers as follows:
file:[Directory]:[Opacity]
Example:
file:/home/klange/wallpapers/sidea.png:100
And separate them with commas.
It's best to make sure all of your wallpapers are the same resolution as your desktop, otherwise I've heard problems will occur.

That's about it. If it doesn't seem to be working, try restarting your computer. The first time I did this, the changes didn't seem to take effect the first time around.

*Gah! I can't seem to get "HOWTO" into the title, which is odd because the first time I edited it (the title was incomplete) it worked fine. It would be nice if a mod could add it in, as I fear people might mistake it for a question thread.*

This does not have to do with wallpapers but I was wondering if you could tell me how you added the clock, CPU usage monitor, and weather. etc. to the right side of the desktop. I have been trying to do this but have not been able to figure it out. Some simple setting somewhere?? Anyway, any help would be appreciated. By the way, thanks for the info on the different wallpapers...:)

---

### Post by oneadvent on 2007-11-14
Those are screenlets. You can download different screenlets from gnome-look.org

---

### Post by SagaLhan on 2007-11-14
Hey there, I really like having different wallpapers on each side of the cube and immediately ditched my icons when I found out how to do it.

Anyway I tried what was described in the first post and compiled Nautilus and everything seemed to work, except the terminal was hanging at (one of) the last file roller. I then let it alone for a few hours to see if it was just busy with something but nothing happened.

Is there any way I can resolve this? Thanks for the time and effort!

[add]

Code copy pasted from my terminal:
```

-e Downloading libeel 2.20 source...           [ DONE ]
-e Downloading Nautilus 2.20 source...         [ DONE ]
-e Building libeel...                          [sudo] password for sagalhan:
[ DONE ]
-e Building Nautilus...                        libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgnomevfs-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `-version-info/-version-number' is ignored for convenience libraries
nautilus-desktop-window.c: In function &#8216;nautilus_desktop_window_new&#8217;:
nautilus-desktop-window.c:130: warning: passing argument 1 of &#8216;gtk_widget_set_colormap&#8217; from incompatible pointer type
Cache file created successfully.
Cache file created successfully.
Cache file created successfully.
Cache file created successfully.
Cache file created successfully.
[ DONE ]
-e Reinstalling file-roller...                 

```

It's been like this for some time, seems to have hanged somehow.

---

### Post by smartboyathome on 2007-11-17
Looks like there are some bad folders. Also, I would just take out reinstalling file-roller as it doesn't work (it isn't called aptitude reinstall). I am working on this script (since it isn't working for me, either), and will post it once I get it done.

---

### Post by hotroddude on 2007-11-18
I take it we cant do this with beryl?

---

### Post by SagaLhan on 2007-11-19
> **smartboyathome said:**
> Looks like there are some bad folders. Also, I would just take out reinstalling file-roller as it doesn't work (it isn't called aptitude reinstall). I am working on this script (since it isn't working for me, either), and will post it once I get it done.

Thanks, hope to see that code soon. Would be really nice to have different wallpapers and icons. =)

---

### Post by grozni on 2007-11-23
I have same package error as maindian523 and pt123 had on first page. What should I do? I tried sudo apt-get build-dep nautilus, I received E: You must put some 'source' URIs in your sources.list. Any help appreciated

---

### Post by drafael on 2007-11-23
Huh.. Tried this twice now, once on gutsy and once on a fresh install of gutsy. Everything builds ok, a few messages from the script with warnings but that's it (unfortunately I didn't save those), and I end up with working everything except - I can't for the life of me find the wallpaper plugin in ccsm.. Am I missing something obvious here? I'll happily give more information but at present I really don't know what's required :|

Edit: I really should say thanks for taking the time to do this, at any rate ^^

---

### Post by ghettowarrior on 2007-11-27
hi,

is it possible that someone makes these deb's so that everyone can just install it..? 

or does this trick requires it that the user compiles it on the computer..?

i have tried it 7 times or something like that always the gtk_widget crash,.. 
also on a clean install... whats wrong with that:P ? 

greets daniel

---

### Post by klange on 2007-11-27
I'm sorry the script is so bad, for now, no one should use it. The Nautilus patcher should work fine, though, and I'm pretty sure *aptitude reinstall* is a valid command, I ran it three times when testing the script on my already-patched laptop.

Hasn't Compiz been updated in the repos to the newest stable?

---

### Post by nikoPSK on 2007-11-27
so no way to get any other app to draw icons? Or add a nautilus patch to make it draw the wallpaper and icons seperatly.

---

### Post by DutchKillerBee on 2007-12-02
> **ghettowarrior said:**
> hi,

is it possible that someone makes these deb's so that everyone can just install it..? 

or does this trick requires it that the user compiles it on the computer..?

i have tried it 7 times or something like that always the gtk_widget crash,.. 
also on a clean install... whats wrong with that:P ? 

greets daniel

Are there any .debs available?
Thanx :)

---

### Post by nikoPSK on 2007-12-02
no, it's a script. if you're in feisty you can grab the wallpaper plugin though synaptic, plugins-unsupported.

But gutsy doesn't have that package.

---

### Post by wormkid on 2007-12-12
I can't compile eel.

with .configure, I got message

```
No package 'gail' found
No package 'gdk-pixbuf-2.0' found
No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-desktop-2.0' found
```

on synaptic, I found libgail. 
what's wrong with me?

event 'sudo apt-get build-dep nautilus' doesn't work!
it says, 'can't find nautilus package'

-------------------------------

it was cause uninstall and installl repeated.
install all with synaptic, and remove completely, and compiled with script.
it works now!

---

### Post by inoxllor on 2007-12-17
There is another way:
Try **wallpapoz**
check it here: [http://ubuntuforums.org/showthread.php?t=69507](http://ubuntuforums.org/showthread.php?t=69507)
or grab the .deb here: [http://www.getdeb.net/app.php?name=Wallpapoz](http://www.getdeb.net/app.php?name=Wallpapoz)

---

### Post by pt123 on 2007-12-17
^ it is really slow for compiz and the plugins

---

### Post by glennric on 2007-12-17
I patched eel and nautilus, and installed the wallpaper plugin, and it works.  I have the desktop showing with, right click works, and there are different wallpapers on every screen.  The problem I have with this is that I have the photowheel and atlantis2 plugins for compiz installed, and have the cube set to become transparent when rotating.  However, the wallpaper plugin doesn't respect this setting.  So I can't see into the cube when rotating with the mouse.  I can get multiple wallpapers that become transparent with the cube background settings, but to see that you have to set nautilus not to show the desktop.  Does anyone know how to get the best of both worlds?  I think that the cube code would have to be modified to get this to work.

---

### Post by BjoeHrn on 2007-12-30
> **SagaLhan said:**
> Hey there, I really like having different wallpapers on each side of the cube and immediately ditched my icons when I found out how to do it.

Anyway I tried what was described in the first post and compiled Nautilus and everything [...]
```

-e Building Nautilus...                        libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgnomevfs-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `-version-info/-version-number' is ignored for convenience libraries
nautilus-desktop-window.c: In function ‘nautilus_desktop_window_new’:
nautilus-desktop-window.c:130: warning: passing argument 1 of ‘gtk_widget_set_colormap’ from incompatible pointer type
Cache file created successfully.
Cache file created successfully.
Cache file created successfully.
Cache file created successfully.
Cache file created successfully.
[ DONE ]
-e Reinstalling file-roller...                 

```

Hi!

I get the same information while compile nautilus with the script. But now it works!
Its so cool to use 4 different wallpapers with icons ;-).

Does anyone know what theses "errors" while compile nautilus mean?

Regards
Bjoern

---

### Post by BuntuFreak on 2008-01-26
Okay I went to COmpiz settings and specified the image files for cube faces. But they don't appear on my cube at all?

What gives?

---

### Post by BuntuFreak on 2008-01-28
I have a question. Sorry if it has been asked before.

If I setup the cube face images in Compiz Settings Manager and then set the desktop background to a transparent image, then my compiz images should bleed through on my cube faces, no?

I'm assuming Nautilus is displaying my background image on top of my Compiz images. I mean if it didn't, then my cubes would have the images I setup. At least that's what I'm thinking.

Of course now my desktop is going to be transparent. Dunno what that means  exactly - perhaps just a black background? Because I cannot have both desktop and cube selected in Compiz, which kinda sucks in a way. Because then - and assuming whatever else I said above is true - that would fix the problem without resorting to any fancy hacks that can potentially damage a nicely working desktop.

Best.

---

### Post by tbannon on 2008-02-02
> **smartboyathome said:**
> Looks like there are some bad folders. Also, I would just take out reinstalling file-roller as it doesn't work (it isn't called aptitude reinstall). I am working on this script (since it isn't working for me, either), and will post it once I get it done.

I too am coming up with the -e Reinstalling file roller ...

Did you ever finish up that script?

Thanks either way.

---

### Post by Yes on 2008-02-10
> **BuntuFreak said:**
> I have a question. Sorry if it has been asked before.

If I setup the cube face images in Compiz Settings Manager and then set the desktop background to a transparent image, then my compiz images should bleed through on my cube faces, no?

I'm assuming Nautilus is displaying my background image on top of my Compiz images. I mean if it didn't, then my cubes would have the images I setup. At least that's what I'm thinking.

Of course now my desktop is going to be transparent. Dunno what that means  exactly - perhaps just a black background? Because I cannot have both desktop and cube selected in Compiz, which kinda sucks in a way. Because then - and assuming whatever else I said above is true - that would fix the problem without resorting to any fancy hacks that can potentially damage a nicely working desktop.

Best.

Nautilus puts a solid color ontop of the wallpaper if you set your background to be a transparent image.

I ran the nautilus patch and it hung at the file-roller.  Is there anything else I need to do, or what?

e:  and will Conky not work with this?  I get this error when I try starting it:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  169
  Current serial number in output stream:  170
```

Thanks =D

---

### Post by cincinnatus13 on 2008-02-14
> **drafael said:**
> Huh.. Tried this twice now, once on gutsy and once on a fresh install of gutsy. Everything builds ok, a few messages from the script with warnings but that's it (unfortunately I didn't save those), and I end up with working everything except - I can't for the life of me find the wallpaper plugin in ccsm.. Am I missing something obvious here? I'll happily give more information but at present I really don't know what's required :|

Edit: I really should say thanks for taking the time to do this, at any rate ^^
ccsm in the app bar and that'll bring it up. Go to cube, click on it, behavior and then look where it says  "add background images." Load up 4 there and they should all be displayed.

---

### Post by syko21 on 2008-02-21
The script worked great but the "archive" option from right click disappeared and the "send to" option disappeared both of which I use frequently. Any idea on how to get them back?

---

### Post by cincinnatus13 on 2008-02-26
Bump for a new problem. I'm just trying to do the nautilus workaround because I have no need for any icons on my desktop anyway. I get everything set up ok but once I restart, the desktop is no longer active (because I disabled it of course). Thing is, I need to find someway to enable Compiz again but every other time I've just right clicked on the desktop to change the effects manager. Anybody know how to get into that without right clicking on the desktop?

Edit: nevermind, one minute of searching and I find it.

---

### Post by cincinnatus13 on 2008-02-26
Well, I tried it but it didn't work. Everytime I would try to spin the cube, it would revert to "no desktop effects enabled." I could never get it to work so if anybody has any suggestions, I'm all ears.

---

### Post by pt123 on 2008-02-28
I have opened a "thread" on the new Ubuntu Ideas website on having different wallpapers on on the workspaces. Please log in and vote for it
[http://brainstorm.ubuntu.com/idea/452/](http://brainstorm.ubuntu.com/idea/452/)

---

### Post by gwoodruff on 2008-02-29
Can anyone tell me how they are making the solid background that nautilus draws with the icons become transparent? I have patched nautilus and eel. I can get 4 different wallpapers by disabling nautilus desktop, but when enabled I get whatever is selected through System/Preferences/Appearance/Background. Any help would be greatly appreciated

---

### Post by metalf8801 on 2008-03-01
> **WindowsSucks said:**
> A couple of people have asked me how I did it, and the answer is simply "there was a tutorial", but that tutorial (link *was* in my sig) is a pretty bleak thing for some Ubuntu users who have no idea where to begin, so here I am writing a better one, tuned specifically to Ubuntu.
**This script may cause you problems. Do not use it unless you know what you're doing. The Cube plugin includes options for wallpapers built-in, use this instead.**

[[img]http://images.ogunderground.com/gal/Halo_3/_thb_cube_full.png[/img][img]http://images.ogunderground.com/gal/Halo_3/_thb_cube_full_b.png[/img]](http://images.ogunderground.com/index.php?spgmGal=Halo_3)
The following bash script will download and install Compiz 0.6.2, with the wallpaper plugin, get the source for Nautilus 2.2 and eel, apply the patches, compile both, and maintain the standard Ubuntu Compiz starter script. It shouldn't print anything other than the status lines unless there are errors.
**EDIT**: WARNING! Be sure to _remove_ Compiz before running this script or things can get messy!
*Note: I only tested this once on my laptop, which already had everything. If you have any problems, let me know.*
```
#!/bin/bash
#       "blah blah blah blah                          \c"
# echo "[ DONE ]"                                      
echo -e "Backing up Compiz execution script...        \c"
sudo mv /usr/bin/compiz /usr/bin/compiz_TEMP  1>/dev/null
echo "[ DONE ]"
echo -e "Installing prerequisites...                  \c"
sudo apt-get install build-essential gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev python-dev python-pyrex 1>/dev/null
echo "[ DONE ]"
echo -e "Downloading tarbells...                      \c"
wget -r -np -nd --accept=tar.bz2 http://releases.compiz-fusion.org/0.6.0/ 2>/dev/null
echo "[ DONE ]"
echo -e "Building Compiz 0.6.2...                     \c"
tar jxvf compiz-0.6.2.tar.bz2 1>/dev/null
cd compiz-0.6.2/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Compiz Bcop...                      \c"
tar jxvf compiz-bcop-0.6.0.tar.bz2 1>/dev/null
cd compiz-bcop-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building libcompizconfig...                  \c"
tar jxvf libcompizconfig-0.6.0.tar.bz2 1>/dev/null
cd libcompizconfig-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compizconfig-python...              \c"
tar jxvf compizconfig-python-0.6.0.tar.bz2 1>/dev/null
cd compizconfig-python-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building ccsm...                             \c"
tar jxvf ccsm-0.6.0.tar.bz2 1>/dev/null
cd ccsm-0.6.0/
sudo python setup.py install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compiz-fusion-plugins-main...       \c"
tar jxvf compiz-fusion-plugins-main-0.6.0.tar.bz2 1>/dev/null
cd compiz-fusion-plugins-main-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compuz-fusion-plugins-extra...      \c"
tar jxvf compiz-fusion-plugins-extra-0.6.0.tar.bz2 1>/dev/null
cd compiz-fusion-plugins-extra-0.6.0/
./configure --prefix=/usr 1>/dev/null
sudo make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building -plugins-unsupported...             \c"
tar jxvf compiz-fusion-plugins-unsupported-0.6.0.tar.bz2 1>/dev/null
cd compiz-fusion-plugins-unsupported-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building compizconfig-backend-gconf...       \c"
tar jxvf compizconfig-backend-gconf-0.6.0.tar.bz2 1>/dev/null
cd compizconfig-backend-gconf-0.6.0/
./configure --prefix=/usr 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Restoring compiz starter...                 \c"
sudo mv /usr/bin/compiz /usr/bin/compiz.real 1>/dev/null
sudo mv /usr/bin/compiz_TEMP /usr/bin/compiz 1>/dev/null
echo "[ DONE ]"
echo -e "Downloading libeel 2.20 source...           \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Downloading Nautilus 2.20 source...         \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Building libeel...                          \c"
tar jxvf eel-2.20.0.tar.bz2 1>/dev/null
cd eel-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/eel.patch 2>/dev/null
patch -p1 < eel.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Nautilus...                        \c"
tar jxvf nautilus-2.20.0.tar.bz2 1>/dev/null
cd nautilus-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/nautilus.patch 2>/dev/null
patch -p1 < nautilus.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Reinstalling file-roller...                 \c"
sudo aptitude reinstall file-roller 1>/dev/null
echo "[ DONE ]"

```

After that, just restart (to ensure that everything is running properly), open up CCSM, enable the Wallpaper plugin and add your wallpapers as follows:
file:[Directory]:[Opacity]
Example:
file:/home/klange/wallpapers/sidea.png:100
And separate them with commas.
It's best to make sure all of your wallpapers are the same resolution as your desktop, otherwise I've heard problems will occur.

That's about it. If it doesn't seem to be working, try restarting your computer. The first time I did this, the changes didn't seem to take effect the first time around.

*Gah! I can't seem to get "HOWTO" into the title, which is odd because the first time I edited it (the title was incomplete) it worked fine. It would be nice if a mod could add it in, as I fear people might mistake it for a question thread.*


**Nautilus Patching Script**:
```
echo -e "Downloading libeel 2.20 source...           \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/eel/2.20/eel-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Downloading Nautilus 2.20 source...         \c"
wget -np -nd http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.20/nautilus-2.20.0.tar.bz2 2>/dev/null
echo "[ DONE ]"
echo -e "Building libeel...                          \c"
tar jxvf eel-2.20.0.tar.bz2 1>/dev/null
cd eel-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/eel.patch 2>/dev/null
patch -p1 < eel.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Building Nautilus...                        \c"
tar jxvf nautilus-2.20.0.tar.bz2 1>/dev/null
cd nautilus-2.20.0/
wget -np -nd http://files.ogunderground.com/compiz_wallpapers/nautilus.patch 2>/dev/null
patch -p1 < nautilus.patch 1>/dev/null
./configure 1>/dev/null
make 1>/dev/null
sudo make install 1>/dev/null
cd ../
echo "[ DONE ]"
echo -e "Reinstalling file-roller...                 \c"
sudo aptitude reinstall file-roller 1>/dev/null
echo "[ DONE ]"
```

Thats really cool thanks for posting

---

### Post by gwoodruff on 2008-03-03
Well, I was using the wallpaper utility built into compiz and just recompiled nautilus and eel, fileroller. I had the cube and 4 different wallpapers but could not get the wallpaper options in System/Preferences/Appearance/Background display a transparent background and Icons.
  I downloaded & followed instructs and un-installed compiz, ran script with no errors and now cannot enable cube! Appearances applet freezes when trying to select anything but none in visual effects.

---

### Post by cggaret on 2008-03-23
I've uninstalled, reinstalled, repatched, and re-everything else several times now, and all attempts result in the same situation: I can only see the 4 separate desktops when opacity is set to 0 in the Desktop cube plugin, and then the icons disappear.  I see on several forums that others have had this problem.  Has anyone worked through this problem?  I believe that it may be just a simple setting somewhere.  Could someone post their successful settings for the desktop cube and wallpaper plugins?  Are you using a solid color or in image as your gnome desktop background?  Does the patch cause the nautilus desktop to always be transparent?  Can it be changed back without reinstalling Nautilus?

---

### Post by Sephoroth on 2008-03-26
I'm having the same problem and I have the same last 3 questions.

Every time I compile Nautilus I end up with
```
libgtk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgdk-x11-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libatk-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgdk_pixbuf-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libpangocairo-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libpango-1.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libcairo.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgnomevfs-2.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgconf-2.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libORBit-2.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libglib-2.0.la' seems to be moved
libtool: link: warning: `-version-info/-version-number' is ignored for convenience libraries
nautilus-desktop-window.c: In function ‘nautilus_desktop_window_new’:
nautilus-desktop-window.c:130: warning: passing argument 1 of ‘gtk_widget_set_colormap’ from incompatible pointer type

```

---

