---
title: "How to get rid of Nautilus?"
date: 2011-01-02
forum: Desktop Environments
---

### Post by tezer on 2011-01-02
Hi all,

I am using Xfce (Xubuntu) and some time ago occasionally installed Nautilus. I wouldn't mind having it on my disk, but struggle between Nautilus and Thunar for desktop management was annoying and I decided to remove Nautilus. 
Now Nautilus is gone, but every time I start my computer the start up screen (with a running mouse) says "Starting Nautilus" and does (tries to do?) something for about 10 seconds. After that it proceeds with autostart.
The problem isn't big and I don't mind waiting for a little more every time Xfce starts, but I guess it should be quite easy to just remove a line somewhere in a config file.
So the question is, what I should edit to make my Xfce forget about Nautilus?

---

### Post by mcduck on 2011-01-02
I can't really say much about XFCE's autostart (apart from the obvious, check the XFCE Session Manager), but the problem with Nautilus trying to take over the desktop is easily solved by changing it's launch command to "*nautilus --no-desktop*"

---

### Post by tezer on 2011-01-02
Thank for reply, but neither Xfce Settings nor autostart have anything related to Nautilus. The message (Starting Nautilus) comes before autostart.

---

### Post by ajgreeny on 2011-01-02
Did you purge nautilus or just remove it?   Purging may be needed to get rid of the various configuration files it will leave behind on a normal ```
sudo apt-get remove
```so try ```
sudo apt-get remove --purge nautilus
```

---

### Post by tezer on 2011-01-02
> **ajgreeny said:**
> Did you purge nautilus or just remove it?   Purging may be needed to get rid of the various configuration files it will leave behind on a normal ```
sudo apt-get remove
```so try ```
sudo apt-get remove --purge nautilus
```

Thanks but it made no difference. I restarted my computer and still "Starting nautilus".

---

### Post by tezer on 2011-01-03
Any other ideas? What script is run before autostart?

---

### Post by tezer on 2011-01-04
Anyone?

---

### Post by tezer on 2011-01-04
In ~/.cache/sessions I found file xfce4-session-compname:0 with four lines containing "nautilus":
```
Client0_CloneCommand=nautilus
Client0_DiscardCommand=/bin/rm,-rf,/home/username/.config/session-state/nautilus-1292007222.desktop
Client0_Program=nautilus
Client0_RestartCommand=nautilus,--sm-client-id,2b7bf197d-6c39-47cd-a3cc-f9c83d7a7c1a
```
I tried to comment them out with # but nothing changed: after re-logging in the file was the same("Starting nautilus" also appeared at start up)

---

### Post by tezer on 2011-01-05
Output of sudo find / -type f -name *nautilus* is:

```
/usr/share/locale-langpack/en_GB/LC_MESSAGES/nautilus-share.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/nautilus-sendto.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/nautilus.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/nautilus-sendto.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/nautilus.mo
/usr/share/locale-langpack/en@shaw/LC_MESSAGES/nautilus-sendto.mo
/usr/share/locale-langpack/en@shaw/LC_MESSAGES/nautilus.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/nautilus-share.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/nautilus-sendto.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/nautilus.mo
/usr/share/app-install/icons/nautilus-cd-burner.png
/usr/share/app-install/icons/nautilus-scripts-manager.svg
/usr/share/app-install/icons/nautilus-pastebin.png
/usr/share/app-install/icons/nautilus-actions.png
/usr/share/app-install/desktop/nautilus-cd-burner.desktop
/usr/share/app-install/desktop/nautilus-pastebin-configurator.desktop
/usr/share/app-install/desktop/nautilus-scripts-manager.desktop
/usr/share/gnome/help/user-guide/C/figures/nautilus_restore_saved_search.png
/usr/share/gnome/help/user-guide/C/gosnautilus.xml
/usr/share/gnome/help-langpack/user-guide/en_AU/gosnautilus.xml
/usr/share/gnome/help-langpack/user-guide/en_CA/gosnautilus.xml
/usr/share/mime/application/x-nautilus-link.xml
/usr/lib/python2.6/dist-packages/ubuntutweak/modules/nautilus.py
/usr/lib/python2.6/dist-packages/ubuntutweak/modules/nautilus.pyc
/home/username/.config/session-state/nautilus-1292007222.desktop
/home/username/.local/share/Trash/info/.nautilus.trashinfo
/home/username/.gnome2/accels/nautilus
/home/username/Downloads/Apps/Utilities/Dropbox/nautilus-dropbox-0.6.2.tar.bz2
/var/lib/dpkg/info/nautilus-data.postrm
/var/lib/dpkg/info/nautilus-data.list
/var/lib/dpkg/info/libnautilus-extension1.postrm
/var/lib/dpkg/info/nautilus.postrm
/var/lib/dpkg/info/libnautilus-extension1.list
/var/lib/dpkg/info/nautilus.list
```

Any ideas?

---

### Post by tezer on 2011-01-06
What can write to ~/.cache/sessions/xfce4-session-compname:0

It gets overwritten every time I log in.

---

### Post by tezer on 2011-01-09
up

---

### Post by cipherboy_loc on 2011-01-09
This looks interesting:
/home/username/.config/session-state/nautilus-1292007222.desktop

What is in it? Try this:

```

mv ~/.config/session-state/nautilus-*.desktop ~/

```



Cipherboy

---

### Post by LewRockwellFAN on 2011-01-09
OP, please let us know your progress. I also would like to get rid of Nautilus because of the memory leak. So far all I've done is make scripts to start some alternate file browsers in my /media folder. Thunar and rox-filer (which can do a desktop too) both seem pretty good but I haven't tried alternate desktops yet.

---

### Post by tezer on 2011-01-10
> **cipherboy_loc said:**
> This looks interesting:
/home/username/.config/session-state/nautilus-1292007222.desktop

What is in it? Try this:

```

mv ~/.config/session-state/nautilus-*.desktop ~/

```



Cipherboy

Thanks, but ~/.config/session-state/ is empty...

---

### Post by tezer on 2011-01-12
My hope never dies...
Just any (crazy!) ideas to try?

---

### Post by tezer on 2011-01-12
My hope never dies...
Just any (crazy!) ideas to try?

---

### Post by cipherboy_loc on 2011-01-12
Crazy ideas? Try:

```

sudo apt-get install nautilus
sudo apt-get purge nautilus

```



Cipherboy

---

### Post by tezer on 2011-01-14
> **cipherboy_loc said:**
> Crazy ideas? Try:

```

sudo apt-get install nautilus
sudo apt-get purge nautilus

```



Cipherboy

No, it didn't work. Probably just not crazy enough...

---

### Post by cipherboy_loc on 2011-01-14
> **tezer said:**
> No, it didn't work. Probably just not crazy enough...

What does:
```
find * .* | grep -i 'nautilus'
```

give you?


Do you have the GNOME start up utility installed? Remove nautilus from there and if there is one for XFCE, remove it from there too.



Cipherboy

---

### Post by cipherboy_loc on 2011-01-14
> **tezer said:**
> No, it didn't work. Probably just not crazy enough...

What does:
```
find * .* | grep -i 'nautilus'
```

give you?


Do you have the GNOME start up utility installed? Remove nautilus from there and if there is one for XFCE, remove it from there too.



Cipherboy

---

### Post by tezer on 2011-01-15
> **cipherboy_loc said:**
> What does:
```
find * .* | grep -i 'nautilus'
```

give you?


Do you have the GNOME start up utility installed? Remove nautilus from there and if there is one for XFCE, remove it from there too.



Cipherboy

After purging Nautilus this command gives me:


```
Downloads/Apps/Utilities/Dropbox/nautilus-dropbox-0.6.2.tar.bz2
./.config/session-state/nautilus-1295088833.desktop
./.gconf/apps/nautilus
./.gconf/apps/nautilus/desktop-metadata
./.gconf/apps/nautilus/desktop-metadata/SETTING@46@volume
./.gconf/apps/nautilus/desktop-metadata/SETTING@46@volume/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/LXFDVD140@46@volume
./.gconf/apps/nautilus/desktop-metadata/LXFDVD140@46@volume/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/2@46@0@32@GB@32@Filesystem@46@volume
./.gconf/apps/nautilus/desktop-metadata/2@46@0@32@GB@32@Filesystem@46@volume/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/READER@46@volume
./.gconf/apps/nautilus/desktop-metadata/READER@46@volume/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume
./.gconf/apps/nautilus/desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/directory
./.gconf/apps/nautilus/desktop-metadata/directory/%gconf.xml
./.gconf/apps/nautilus/desktop-metadata/Elements@46@volume
./.gconf/apps/nautilus/desktop-metadata/Elements@46@volume/%gconf.xml
./.gconf/apps/nautilus/%gconf.xml
./.gconf/apps/nautilus/preferences
./.gconf/apps/nautilus/preferences/%gconf.xml
./.local/share/Trash/info/.nautilus.trashinfo
./.local/share/Trash/files/.nautilus
./.nautilus
./.gnome2/nautilus-scripts
./.gnome2/accels/nautilus
./Downloads/Apps/Utilities/Dropbox/nautilus-dropbox-0.6.2.tar.bz2
./.cache/sessions/bak/nautilus-1292007222.desktop
../xtez/.config/session-state/nautilus-1295088833.desktop
../xtez/.gconf/apps/nautilus
../xtez/.gconf/apps/nautilus/desktop-metadata
../xtez/.gconf/apps/nautilus/desktop-metadata/SETTING@46@volume
../xtez/.gconf/apps/nautilus/desktop-metadata/SETTING@46@volume/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/LXFDVD140@46@volume
../xtez/.gconf/apps/nautilus/desktop-metadata/LXFDVD140@46@volume/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/2@46@0@32@GB@32@Filesystem@46@volume
../xtez/.gconf/apps/nautilus/desktop-metadata/2@46@0@32@GB@32@Filesystem@46@volume/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/READER@46@volume
../xtez/.gconf/apps/nautilus/desktop-metadata/READER@46@volume/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume
../xtez/.gconf/apps/nautilus/desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/directory
../xtez/.gconf/apps/nautilus/desktop-metadata/directory/%gconf.xml
../xtez/.gconf/apps/nautilus/desktop-metadata/Elements@46@volume
../xtez/.gconf/apps/nautilus/desktop-metadata/Elements@46@volume/%gconf.xml
../xtez/.gconf/apps/nautilus/%gconf.xml
../xtez/.gconf/apps/nautilus/preferences
../xtez/.gconf/apps/nautilus/preferences/%gconf.xml
../xtez/.local/share/Trash/info/.nautilus.trashinfo
../xtez/.local/share/Trash/files/.nautilus
../xtez/.nautilus
../xtez/.gnome2/nautilus-scripts
../xtez/.gnome2/accels/nautilus
../xtez/Downloads/Apps/Utilities/Dropbox/nautilus-dropbox-0.6.2.tar.bz2
../xtez/nautilusfind.txt
../xtez/.cache/sessions/bak/nautilus-1292007222.desktop
.cache/sessions/bak/nautilus-1292007222.desktop
.gconf/apps/nautilus
.gconf/apps/nautilus/desktop-metadata
.gconf/apps/nautilus/desktop-metadata/SETTING@46@volume
.gconf/apps/nautilus/desktop-metadata/SETTING@46@volume/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/LXFDVD140@46@volume
.gconf/apps/nautilus/desktop-metadata/LXFDVD140@46@volume/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/2@46@0@32@GB@32@Filesystem@46@volume
.gconf/apps/nautilus/desktop-metadata/2@46@0@32@GB@32@Filesystem@46@volume/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/READER@46@volume
.gconf/apps/nautilus/desktop-metadata/READER@46@volume/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume
.gconf/apps/nautilus/desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/directory
.gconf/apps/nautilus/desktop-metadata/directory/%gconf.xml
.gconf/apps/nautilus/desktop-metadata/Elements@46@volume
.gconf/apps/nautilus/desktop-metadata/Elements@46@volume/%gconf.xml
.gconf/apps/nautilus/%gconf.xml
.gconf/apps/nautilus/preferences
.gconf/apps/nautilus/preferences/%gconf.xml
.gnome2/nautilus-scripts
.gnome2/accels/nautilus
.local/share/Trash/info/.nautilus.trashinfo
.local/share/Trash/files/.nautilus
.nautilus
```

Folder.nautilus is empty,

---

### Post by tezer on 2011-01-15
Some update on what I other tricks I tried:

added the following lines to my *~/.local/share/applications/defaults.list* so that Thunar is used to open folders by gvfs-open:
```
x-directory/gnome-default-handler=Thunar.desktop
inode/directory=Thunar.desktop
x-directory/normal=Thunar.desktop
```

I also tried reinstalling nautilus and running it with 
*nautilus --sm-disable*
It solved the problem of automatic modification of file *.cache/sessions/xfce4-session-compname:0*  but nautilus still starts every time I log in. And it is not possible to stop it even with *nautilus -q* it keeps restarting itself every time.
It looks like I need to get rid of gnome-session-bin altogether, but I am afraid it may damage my Xfce desktop as it will remove gdm and xubuntu-desktop.
Nautilus behaves just like a virus... I don't really want to re-install my system, but Nautilus starting every time I load my Xfce is annoying.

---

### Post by tezer on 2011-01-15
On [forum.xfce.org]("http://forum.xfce.org") I was advised to remove *~/.cache/sessions* folder. 
Looks like deleting the whole *~/.cache* helped (I overdid it a little). Although new *~/.cache/sessions* (with Nautilus mentioned in several lines) was created on log out and I failed to delete being logged out (didn't have permissions to do so), after the next log in there was no "Starting nautilus" annoyance. I checked the session file, it still mentioned Nautilus. After another log-out log-in routine the file changed again and did not have any strings with Nautilus.

To be honest, I don't know what happened and what was changing the file, but I am glad I've got rid of the annoyance.
Thank to all who offered help and advice (including crazy ones:)).

---

