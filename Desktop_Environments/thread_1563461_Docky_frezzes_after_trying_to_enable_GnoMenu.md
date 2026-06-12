---
title: "Docky frezzes after trying to enable GnoMenu"
date: 2010-08-29
forum: Desktop Environments
---

### Post by ewuldoxx on 2010-08-29
Hello there. I'd like to have GnoMenu in my Docky dockbar. I have installed both docky and gnomenu from their ppa's. I've found GnoMenu helper in Docky's helpers list, but when i try to run it, my docky freezes and i must restart it. where could be the problem? i hope you got what i mena : )

---

### Post by Raavea on 2010-09-12
I believe I have the same issue as the above poster..

 I have installed Gnomenu 2.9 from the [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu) repository, and the Docky helper would not do anything, even after a restart.

 Then I attempted to build from the source, downloaded from their launchpad ([https://launchpad.net/gnomenu);](https://launchpad.net/gnomenu);)
 ```
userr@compeeper:~/gnomenu$ sudo make install
install -d /etc/gnomenu /usr/bin/ /usr/lib \
	/usr/share /usr/lib/bonobo/servers /usr/share/cairo-dock/plug-ins/Dbus/third-party/GnoMenu /usr/share/kde4/apps/plasma
python -u setup.py
Preparing to install translation
/home/userrr/gnomenu/po
installing translations
Creating language Binary for : gnomenu-pl
Creating language Binary for : gnomenu-oc
Creating language Binary for : gnomenu-yi
Creating language Binary for : gnomenu-ca
Creating language Binary for : gnomenu-pt_BR
Creating language Binary for : gnomenu-ml
Creating language Binary for : gnomenu-tr
Creating language Binary for : gnomenu-nb
Creating language Binary for : gnomenu-tet
Creating language Binary for : gnomenu-sv
Creating language Binary for : gnomenu-nl
Creating language Binary for : gnomenu-ja
Creating language Binary for : gnomenu-uk
Creating language Binary for : gnomenu-fr
Creating language Binary for : gnomenu-zh_CN
Creating language Binary for : gnomenu-ko
Creating language Binary for : gnomenu-ru
Creating language Binary for : gnomenu-bg
Creating language Binary for : gnomenu-id
Creating language Binary for : gnomenu-de
Creating language Binary for : gnomenu-sr
Creating language Binary for : gnomenu-es
Creating language Binary for : gnomenu-da
Creating language Binary for : gnomenu-pt
Creating language Binary for : gnomenu-hu
Creating language Binary for : gnomenu-cs
Creating language Binary for : gnomenu-zh_TW
Creating language Binary for : gnomenu-lt
Creating language Binary for : gnomenu-ia
Creating language Binary for : gnomenu-ar
Creating language Binary for : gnomenu-fi
Creating language Binary for : gnomenu-el
Creating language Binary for : gnomenu-he
Creating language Binary for : gnomenu-gl
Creating language Binary for : gnomenu-ro
Creating language Binary for : gnomenu-it
Creating language Binary for : gnomenu-sk
#-install src/bin/GnoMenu.py /usr/bin/
cp -r src/lib/gnomenu /usr/lib
cp -r src/share/gnomenu /usr/share
cp -r src/share/avant-window-navigator /usr/share
install src/share/dockmanager/scripts/GnoMenu.py /usr/share/dockmanager/scripts/
cp -r src/share/dockmanager/scripts/GnoMenu /usr/share/dockmanager/scripts/
#-cp -r src/share/xfce4 /usr/share
cp -r src/share/locale /usr/share
#-cp -r src/share/plasma/plasmoids /usr/share/kde4/apps/plasma
install src/share/cairo-dock/third-party/GnoMenu/* /usr/share/cairo-dock/plug-ins/Dbus/third-party/GnoMenu/
#-cp -r src/share/cairo-dock ~/.config/
install src/bin/GnoMenu.py /usr/bin/
install src/lib/bonobo/GNOME_GnoMenu.server /usr/lib/bonobo/servers
plasmapkg -i src/share/plasma/plasmoids/GnoMenu.zip -p /usr/share/kde4/apps/plasma/plasmoids
make: plasmapkg: Command not found
make: [install] Error 127 (ignored)
Makefile: GnoMenu installed.
```
 Now, both ways, the gnomenu will work on a normal, gnome panel, but of course that's what I want to get away from by using Docky with Gnomenu!
 I am unsure what that plasmapkg thing is, perhaps I ought to go try and install it?

 Anyway, now, after restarting Docky, the helper says 'Running' but Docky freezes. So I restart Docky, and nothing happens. I go into helpers and it's Stopped but the enable icon is actually a disable icon and it doesn't display or anything. Clicking it so it's 'Running' again causes more freezing.

 I'll update if that (plasmapkg) works, but I'd love to hear advice or just someone else's experience. (Will it ever work, should I just give up?)

---

### Post by fabounet on 2010-09-13
If you want to use GnoMenu with a dock, you can try GLX-Dock, the GnoMenu applet is working as it should.

---

### Post by kerry_s on 2010-09-13
it works in awn to, even dockbarx works in awn.

---

