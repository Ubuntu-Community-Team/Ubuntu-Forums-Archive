---
title: "Favorite launchers not remembered in Unity, can't edit dconf-editor"
date: 2011-09-11
forum: Desktop Environments
---

### Post by silentstone on 2011-09-11
My pinned applications in the Unity Launcher are removed each reboot.  Instead, the defaults--Home, Firefox, LibreOffice (3), Ubuntu Software Center, Ubuntu One--reappear.  I can add and remove applications during a desktop session, but once I reboot, the default returns.  I can't edit the favorites list in **dconf-editor**.  Any changes I make disappear once focus is removed from that text field. Trying it from the terminal, with **gsettings**:

```
mute@mouse:/mnt/lucid/home/mute$ gsettings list-keys com.canonical.Unity.Launcher
favorite-migration
favorites
shows-on-edge
mute@mouse:/mnt/lucid/home/mute$ gsettings get com.canonical.Unity.Launcher favorites['ubiquity-gtkui.desktop', 'nautilus-home.desktop', 'firefox.desktop', 'libreoffice-writer.desktop', 'libreoffice-calc.desktop', 'libreoffice-impress.desktop', 'ubuntu-software-center.desktop', 'ubuntuone-control-panel-gtk.desktop']
mute@mouse:/mnt/lucid/home/mute$ gsettings writable com.canonical.Unity.Launcher favoritestrue
mute@mouse:/mnt/lucid/home/mute$ gsettings set com.canonical.Unity.Launcher favorites ['ubiquity-gtkui.desktop', 'nautilus-home.desktop', 'firefox.desktop', 'ubuntuone-control-panel-gtk.desktop', 'conkeror.desktop']
Usage:
  gsettings set SCHEMA[:PATH] KEY VALUE

Set the value of KEY to VALUE

Arguments:
  SCHEMA    The name of the schema
  PATH      The path, for relocatable schemas
  KEY       The key within the schema
  VALUE     The value to set

```

---

### Post by Krytarik on 2011-09-11
This should fix it all:

[http://www.tuxgarage.com/2011/07/unity-reset-after-restart-relogin.html](http://www.tuxgarage.com/2011/07/unity-reset-after-restart-relogin.html)

Greetings.

---

### Post by silentstone on 2011-09-12
_libdconf0_ was already installed, so I reinstalled it.  Didn't work.  I made a log of the Unity reset after that:

> 
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libccp.so : No such file or directory
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libbailer.so : No such file or directory
Initializing bailer options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libdetection.so : No such file or directory
Initializing detection options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libcomposite.so : No such file or directory
Initializing composite options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libopengl.so : No such file or directory
Initializing opengl options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libdecor.so : No such file or directory
Initializing decor options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libmousepoll.so : No such file or directory
Initializing mousepoll options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libvpswitch.so : No such file or directory
Initializing vpswitch options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libregex.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libanimation.so : No such file or directory
Initializing animation options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libsnap.so : No such file or directory
Initializing snap options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libexpo.so : No such file or directory
Initializing expo options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libmove.so : No such file or directory
Initializing move options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libcompiztoolbox.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libplace.so : No such file or directory
Initializing place options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libgrid.so : No such file or directory
Initializing grid options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libimgpng.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libgnomecompat.so : No such file or directory
Initializing gnomecompat options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libwall.so : No such file or directory
Initializing wall options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libezoom.so : No such file or directory
Initializing ezoom options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libworkarounds.so : No such file or directory
Initializing workarounds options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libstaticswitcher.so : No such file or directory
Initializing staticswitcher options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libresize.so : No such file or directory
Initializing resize options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libfade.so : No such file or directory
Initializing fade options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libunitymtgrabhandles.so : No such file or directory
Initializing unitymtgrabhandles options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libscale.so : No such file or directory
Initializing scale options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libsession.so : No such file or directory
Initializing session options...done
compiz (core) - Debug: Could not stat() file /home/mute/.compiz-1/plugins/libunityshell.so : No such file or directory
/usr/share/themes/Peace/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
** (<unknown>:7677): DEBUG: Unity accessibility initialization
** (<unknown>:7677): DEBUG: Shows on edge: 1

** (<unknown>:7677): WARNING **: Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'

** (<unknown>:7677): WARNING **: Desktop file 'ubiquity-gtkui.desktop' Does not exist anywhere we can find itAnd a bit more, but I'm not sure how to debug this.

I logged into a Unity GUI session as another user, and everything was fine and changeable and retained after a reboot.  So the problem is only with my user, and it seems to be spreading--some gconf settings aren't editable in gconf-editor, the date/time can't even be changed from the Application Menu calendar dropdown, and the desktop theme just lost some parts (icon theme, gtk or window style, panel colors) :eek:

Something got corrupted, but it can't be an installation issue because the problem is only with one user.  Okay, I'm going to check on changed folders in that user...try to track down the glitching files.

---

### Post by ProteinPappa on 2011-10-21
Did you find a solution to this? I'm having the same issue. (Using 11.10 x64.)

---

### Post by silentstone on 2011-11-05
ProteinPappa, I didn't track down the exact cause of the problem.  However, I got it to stop by deleting my config folder and re-configing everything from a fresh session.

---

