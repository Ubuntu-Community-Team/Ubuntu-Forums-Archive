---
title: "AWN quirks"
date: 2009-01-22
forum: General Help
---

### Post by detroit/zero on 2009-01-22
Recently, through no action of my own and for no easily discernable reason, my AWN bar lost all the launchers I had placed there. I had one for Firefox, one for TBird, and one for a Terminal. The launchers and their icons have disappeared. AWN also no longer displays open tasks such as browser windows, running terminals, Synaptic, or anything else.

Dragging and dropping from the gnome-panel menu does not work. It creates an entry in the awn-manager launchers tab, but all the fields are blank. This blank entry cannot be deleted until I edit it and put something in the Name and Command fields. Adding an entry from the AWN-manager Launchers tab is ineffective; no matter what icon, name, and command I enter, the entry is never shown on the AWN bar - not even a blank space or a grey/white line like a broken AWN app tends to show.. it's like it just doesn't exist.

Unable to find a solution through tinkering, I figured a quick purge and reinstall of AWN would do the trick. From my understanding, when you purge something (either using *apt-get remove --purge* from the command line or selecting *Completely Remove* inside Synaptic) it is supposed to remove all traces of the program along with its' configuration files. Much to my surprise, when I did my re-install of AWN, the first time I ran it it re-appeared with all my custom icons and settings.

My main question is: How can I get my launchers back onto the AWN panel?

My secondary question is: If --purge or Completely Remove is supposed to remove a program and all its configuration files, why is AWN reappearing with custom settings that I did before I did my purge? I've noticed this with other things I supposedly "Completely Removed" as well - not just AWN.

Thanks for any help.

**EDIT:** I was going to marked this is solved, but I don't see the "Mark as solved" option under Thread Tools.

---

### Post by reahjw6 on 2009-01-22
[http://ubuntuforums.org/showthread.php?t=762363&highlight=cairo+dock](http://ubuntuforums.org/showthread.php?t=762363&highlight=cairo+dock)

This may help with awn problems.

---

### Post by detroit/zero on 2009-01-23
> **reahjw6 said:**
> [http://ubuntuforums.org/showthread.php?t=762363&highlight=cairo+dock](http://ubuntuforums.org/showthread.php?t=762363&highlight=cairo+dock)

This may help with awn problems.It doesn't. The best advice in 54 pages of thread is to uninstall and reinstall. As I've already said, that doesn't seem to be working for me.

I should have mentioned in my initial post that I did install from reaocards repo using that guide, and that thread was the first thing I looked at when all this first happened.

---

### Post by detroit/zero on 2009-01-23
Addendum:

When using the *apt-get remove --purge* command, this is the result I get:```
zero@zero-laptop:~$ sudo apt-get remove --purge avant-window-navigator-bzr awn-manager-bzr awn-core-applets-bzr libawn0-bzr
[sudo] password for zero: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avant-window-navigator-bzr* awn-core-applets-bzr* awn-manager-bzr*
  libawn0-bzr* python-awn-bzr*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 17.6MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 139965 files and directories currently installed.)
Removing avant-window-navigator-bzr ...
Purging configuration files for avant-window-navigator-bzr ...
dpkg - warning: while removing avant-window-navigator-bzr, directory `/usr/share/avant-window-navigator/schemas' not empty so not removed.
Removing awn-core-applets-bzr ...
Purging configuration files for awn-core-applets-bzr ...
Removing awn-manager-bzr ...
Purging configuration files for awn-manager-bzr ...
dpkg - warning: while removing awn-manager-bzr, directory `/usr/share/avant-window-navigator' not empty so not removed.
Removing python-awn-bzr ...
Removing libawn0-bzr ...
Purging configuration files for libawn0-bzr ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```You can see straightaway that not everything could be removed (why a purge wouldn't remove settings directories because they're not empty is beyond me), but the listed files are not the only ones that aren't being removed:```
zero@zero-laptop:~$ locate awn
/home/zero/.config/awn
/home/zero/.config/autostart/awn.desktop
/home/zero/.config/awn/applets
/home/zero/.config/awn/custom-icons
/home/zero/.config/awn/launchers
/home/zero/.config/awn/themes
/home/zero/.config/awn/applets/BlingSwitcher
/home/zero/.config/awn/applets/BlingSwitcher.desktop
/home/zero/.config/awn/applets/BlingSwitcher/BlingSwitcher.png
/home/zero/.config/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py
/home/zero/.config/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.pyc
/home/zero/.config/awn/applets/BlingSwitcher/Makefile.am
/home/zero/.config/awn/applets/BlingSwitcher/PySwitcher.py
/home/zero/.config/deluge/torrentfiles/Night.of.the.Day.of.the.Dawn.of.the.DVDRip.LRH.3406242.TPB.torrent.fastresume
/home/zero/.gconf/apps/avant-window-navigator/applets/awn-notification-daemon
/home/zero/.gconf/apps/avant-window-navigator/applets/awn-system-monitor
/home/zero/.gconf/apps/avant-window-navigator/applets/awn-notification-daemon/%gconf.xml
/home/zero/.gconf/apps/avant-window-navigator/applets/awn-system-monitor/%gconf.xml
/home/zero/.gnome2/rhythmbox/covers/Concord Dawn - Bitchkiller-LPO004.rb-blist
/home/zero/.gnome2/rhythmbox/covers/Soundtrack - From Dusk Till Dawn.jpg
/home/zero/.icons/awn-theme
/home/zero/.icons/awn-theme/index.theme
/home/zero/.icons/awn-theme/scalable
/home/zero/.icons/awn-theme/scalable/application-exit-quit-1224867622.png
/home/zero/.icons/awn-theme/scalable/gnome-main-menu-main-menu-1224858038.png
/opt/openoffice.org/basis3.0/program/python-core-2.3.4/lib/distutils/spawn.py
/opt/openoffice.org/basis3.0/share/gallery/www-back/lawn-artificial.jpg
/opt/openoffice.org/basis3.0/share/gallery/www-back/lawn.jpg
/usr/bin/awn-applet-activation
/usr/bin/awn-launcher-editor
/usr/bin/awn-manager
/usr/bin/awn-schema-to-gconf
/usr/include/libawn-extras
/usr/include/spawn.h
/usr/include/glib-2.0/glib/gspawn.h
/usr/include/gtk-2.0/gdk/gdkspawn.h
/usr/lib/awn
/usr/lib/libawn-extras.a
/usr/lib/libawn-extras.la
/usr/lib/libawn-extras.so
/usr/lib/libawn-extras.so.0
/usr/lib/libawn-extras.so.0.0.1
/usr/lib/libawn.so.0
/usr/lib/libawn.so.0.0.1
/usr/lib/debug/usr/lib/pulse-0.9/modules/module-esound-compat-spawnfd.so
/usr/lib/debug/usr/lib/pulse-0.9/modules/module-esound-compat-spawnpid.so
/usr/lib/pkgconfig/awn-extras.pc
/usr/lib/pulse-0.9/modules/module-esound-compat-spawnfd.so
/usr/lib/pulse-0.9/modules/module-esound-compat-spawnpid.so
/usr/lib/python2.4/distutils/spawn.py
/usr/lib/python2.4/distutils/spawn.pyc
/usr/lib/python2.5/distutils/spawn.py
/usr/lib/python2.5/distutils/spawn.pyc
/usr/lib/python2.5/site-packages/awn
/usr/share/awn-extras-applets
/usr/share/app-install/desktop/awn-manager.desktop
/usr/share/applications/awn-manager.desktop
/usr/share/avant-window-navigator/awn-manager
/usr/share/avant-window-navigator/schemas/awn.schema-ini
/usr/share/doc/awn-core-applets-bzr
/usr/share/doc/awn-manager-bzr
/usr/share/doc/libawn0-bzr
/usr/share/doc/python-awn-bzr
/usr/share/doc/console-tools/examples/spawn_console.c
/usr/share/doc/console-tools/examples/spawn_login.c
/usr/share/fonts/truetype/ttf-larabie-uncommon/yawnovis.ttf
/usr/share/gconf/schemas/awn-applets-shared.schemas
/usr/share/gconf/schemas/awn-notification-daemon.schemas
/usr/share/gconf/schemas/awn.schemas
/usr/share/gconf/schemas/awnsystemmonitor.schemas
/usr/share/gconf/schemas/awnterm.schemas
/usr/share/icons/hicolor/48x48/apps/awn-manager.png
/usr/share/icons/hicolor/scalable/apps/awn-applet-digital-clock.svg
/usr/share/icons/hicolor/scalable/apps/awn-manager.svg
/usr/share/pixmaps/pidgin/emotes/default/yawn.png
/var/cache/apt/archives/awn-core-applets-bzr_0.3.1.bzr939.1~hardy_i386.deb
/var/cache/apt/archives/awn-manager-bzr_0.3.1.bzr489.3~hardy_i386.deb
/var/cache/apt/archives/libawn0-bzr_0.3.1.bzr489.3~hardy_i386.deb
/var/cache/apt/archives/python-awn-bzr_0.3.1.bzr489.3~hardy_i386.deb
/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_main_source_Sources
/var/lib/apt/lists/partial/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_Release
/var/lib/dpkg/info/awn-core-applets-bzr.list
/var/lib/dpkg/info/awn-core-applets-bzr.md5sums
/var/lib/dpkg/info/awn-core-applets-bzr.postinst
/var/lib/dpkg/info/awn-core-applets-bzr.postrm
/var/lib/dpkg/info/awn-core-applets-bzr.prerm
/var/lib/dpkg/info/awn-core-applets-bzr.shlibs
/var/lib/dpkg/info/awn-manager-bzr.list
/var/lib/dpkg/info/awn-manager-bzr.md5sums
/var/lib/dpkg/info/awn-manager-bzr.postinst
/var/lib/dpkg/info/awn-manager-bzr.postrm
/var/lib/dpkg/info/libawn0-bzr.list
/var/lib/dpkg/info/libawn0-bzr.md5sums
/var/lib/dpkg/info/libawn0-bzr.postinst
/var/lib/dpkg/info/libawn0-bzr.postrm
/var/lib/dpkg/info/libawn0-bzr.shlibs
/var/lib/dpkg/info/python-awn-bzr.list
/var/lib/dpkg/info/python-awn-bzr.md5sums
```I'm still looking for answers to my two questions:
1. How can I regain launcher/tasks ability on my AWN bar; and
2. Why doesn't a purge of a program actually purge everything?

---

### Post by Tomatz on 2009-01-23
Recompile awn from source (git/bzr). I had this problem once after a python update.

---

### Post by detroit/zero on 2009-01-23
> **Tomatz said:**
> Recompile awn from source (git/bzr). I had this problem once after a python update.
I suppose that's as good an answer as any and, truth be told, that is the next logical step that I was hoping to avoid.

However, since "purging" awn from my system leaves all those files behind, isn't a freshly compiled version just going to reappear with all the same problems I'm currently having?

---

### Post by Tomatz on 2009-01-23
> **detroit/zero said:**
> I suppose that's as good an answer as any and, truth be told, that is the next logical step that I was hoping to avoid.

However, since "purging" awn from my system leaves all those files behind, isn't a freshly compiled version just going to reappear with all the same problems I'm currently having?

That is just user config, you can delete them yourself before compiling.

---

### Post by detroit/zero on 2009-01-23
> **Tomatz said:**
> That is just user config, you can delete them yourself before compiling.
Yeah, but the thing is: I've been trying to track down and manually delete those files since last night and I can't find them in a terminal or in a root Nautilus window. The locate command says they're there, and the fact that AWN keeps reappearing with a bunch of custom icons and broken launchers says they're there, but I can't find any trace of any of them anywhere in my system.

Side note: I for some reason can't compile AWN. I get an error about an unmet dependency, but when I search for or try to install the dependency, apt-get says the packages don't exist. (gtk+-2.0 and pygtk-2.0)

---

### Post by Tomatz on 2009-01-23
Ah didn't look down the page. I see you still have ALL of awn. 

I would delete the config etc in **/home/zero** and when you compile it should overwrite the rest.

---

### Post by detroit/zero on 2009-01-23
Yeah, that's the first thing I did after I uninstalled. That folder is easy to find and I always knew it was there.

There's some other hidden folder full of settings or something somewhere else in the system that's not getting removed in the purge.

---

### Post by Tomatz on 2009-01-23
You need to:

```
sudo apt-get install libgtk2.0-0 libgtk2.0-dev python-gtk2-dev python-gtk2
```

When doing **./configure** you wont usually get the package names (as in the repos) just the basic name of the package. Just google them and remember to install the **-dev** package also as it has the development headers needed for compiling.

;)

[B]EDIT:

Re-run that command as i got one of the package names wrong. SORRY :([/B]

---

### Post by detroit/zero on 2009-01-23
> **Tomatz said:**
> You need to:

```
sudo apt-get install libgtk2.0-0 libgtk2.0-dev python-gtk2-dev pygtk-2.0
```
;)
Way ahead of you:```
zero@zero-laptop:~$ sudo apt-get install libgtk2.0-0 libgtk2.0-dev python-gtk2-dev pygtk-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version.
libgtk2.0-dev is already the newest version.
python-gtk2-dev is already the newest version.
python-gtk2-dev set to manually installed.
**E: Couldn't find package pygtk-2.0**
```

---

### Post by detroit/zero on 2009-01-23
Screw all this.

Cairo dock, here I come.

---

### Post by Tomatz on 2009-01-23
> **detroit/zero said:**
> Screw all this.

Cairo dock, here I come.

**That was my fault sorry re run the command. I edited it (above)**

---

### Post by detroit/zero on 2009-01-23
Yeah, thanks anyways. I figured that part of it (renaming the package to python instead of py) on my own. I was going through the readme file that comes with the AWN source download and installing things...

At any rate, I gave it one more shot. I compiled and started awn and it reappeared with all my custom icons and the missing launchers/tasks! I'm not sure where the hidden/secret config files for AWN are residing, but I couldn't find them to save my life.

I've successfully installed and configured cairo-dock and I managed to set it up more or less the way I was used to seeing my AWN bar. It took me a little over an hour, and I suppose I'm happy with the way it works.

I'll leave this thread unsolved since I really didn't solve why AWN keeps files/settings after it's been supposedly "purged" and re-installed.

---

### Post by detroit/zero on 2009-01-23
Well, I found the answer to the missing launchers and task icons.

In the applet tab of awn-manager, not quite halfway through the list of applets, is something called "Launcher/Taskmanager" and its description calls it "the main awn launcher/task manager applet."

I'm not sure how, since it's been a while since I even opened awn-manager, but somehow this applet got deleted from my list. Hence, no launchers or tasks on my bar.

I was honestly going to say goodbye to awn, but it turns out that cairo-dock is an even buggier, and far more annoying POS than AWN isl.

I'll mark this thread as solved, since discussion about *apt-get --purge* aren't really suited to Desktop Effects & Customization.

---

### Post by Ampersand. on 2009-02-17
well im sure glad i finished reading the whole thread. i was all set to say Fk you to AWL and stick with the normal panels. I swear i searched for that exact applet right after accidentally deleting it but it wasnt there soon after. i though i had mistaken the name so i restarted and it still wasnt there. Luckily i read your post and when i checked again, there it was. Mysterious. computers are really crazy sometimes

---

