---
title: "Default file manager"
date: 2011-03-13
forum: Desktop Environments
---

### Post by session13 on 2011-03-13
Hi,

I accidentially replaced default file manager Nautilus with Gnome Commander and now when browsing other hard drives or devices throught *Places* menu it opens in Gnome Commander. How can I revert to Nautilus?

I know its stupid but I couldn't find anything in google.

Thanks

---

### Post by bapoumba on 2011-03-13
How did you change the default file manager ? There are several ways..

Please post the output to:
```
/usr/share/applications/nautilus-folder-handler.desktop
```

Here is mine:
```
bapoumba@SonyBlue:~$ cat /usr/share/applications/nautilus-folder-handler.desktop
[Desktop Entry]
Name=Open Folder
TryExec=nautilus
[COLOR="Green"]Exec=nautilus --no-desktop %U[/COLOR]
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.32.0
X-Ubuntu-Gettext-Domain=nautilus

```

The line to look at is the one in green.

---

### Post by session13 on 2011-03-13
The green line on my linux box is exactly the same:
```
[Desktop Entry]
Name=Open Folder
TryExec=nautilus
Exec=nautilus --no-desktop %U
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus
```I remember only that some program asked me (with dialog box) what I want to use to browse files. I choosed Gnome Commander and from that time GC is my default file manager :(

---

### Post by bapoumba on 2011-03-13
It may help if you remember which application asked you to change the default :)

Anyway (and now I've not tested this, I'll look around), there are other nautilus related files there:
```
bapoumba@SonyBlue:~$ cd /usr/share/applications/
bapoumba@SonyBlue:/usr/share/applications$ ls n*
nautilus-autorun-software.desktop            nautilus-folder-handler.desktop
nautilus-browser.desktop                     nautilus-home.desktop
nautilus-computer.desktop                    network-scheme.desktop
nautilus.desktop                             nm-connection-editor.desktop
nautilus-file-management-properties.desktop

```
Please have a look with cat <filename> if you see anything that says gnome-commander.

---

### Post by Krytarik on 2011-03-13
Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by session13 on 2011-03-19
It was the case :)

In *~/.local/share/applications/mimeapps.list* the entry was:
```
inode/directory=userapp-gnome-commander-AM6HRV.desktop;nautilus-folder-handler.desktop;kde4-kfmclient_dir.desktop;kde4-dolphin.desktop;
```I've changed it to:
```
inode/directory=nautilus-folder-handler.desktop;
```and now all directories open in Nautilus.

Thanks for help

---

