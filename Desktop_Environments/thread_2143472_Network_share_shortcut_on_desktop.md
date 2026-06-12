---
title: "Network share shortcut on desktop"
date: 2013-05-09
forum: Desktop Environments
---

### Post by andlinux on 2013-05-09
Well, I have 3 network shares and I have made 3 different shortcuts on my desktop to go directly to these locations, but since I upgraded from Xubuntu 12.04 to 13.04 I'm not able to open these locations anymore. I always get a message and sometimes another one: 
```
The location isn't mounted
``` or 
```
Starter from untrusted shortcut 
The desktopfile VU+.desktop is standing on an unsecure place and isn't marked as executable. If you do not trust the programma click cancel.
url=smb://192.168.1.4/harddisk
``` [ATTACH=CONFIG]242370[/ATTACH]

If I press on " make an executable" then I get the message like the first one "The location isn't mounted".

(some messages translated from Dutch)

I also made a bookmark in the filemanager, like this: [ATTACH=CONFIG]242371[/ATTACH]
and then I can go to the share but I can't copy/paste or rename. I mean if I press the right mouse then I don't get the options like copy/paste and stuff like that.

How can I solve this ?

---

### Post by Morbius1 on 2013-05-09
Right Click the desktop launcher > Select "Edit Launcher" > and change the command from:
> smb://192.168.1.4/harddisk
To 
```
thunar smb://192.168.1.4/harddisk
```

---

### Post by andlinux on 2013-05-09
I tried that on all the shortcuts but it's not working, it gives a message about a URI shedual.

---

### Post by Morbius1 on 2013-05-09
I can't reproduce your problem.

Open up a terminal and run the command:
```
thunar smb://192.168.1.4/harddisk
```
Same error message?

---

### Post by andlinux on 2013-05-09
No, if I do it in a terminal it's working. 
I also tried: pcmanfm smb://192.168.1.4/harddisk
and that's also working.

EDIT: Only thing that's not working is connecting to my share on my xbmc box, because it uses a username and password but probably with the right command it will work.

Edit2: I'm able to make a starter on the desktop and see the files for 2 devices after I click "make executable", after that click I didn't see the message.

Edit3: It seems that all is working now and I know what was wrong. Before I had url links instead of starters but before those worked :)

---

### Post by Morbius1 on 2013-05-09
Posted past each other it seems.

---

### Post by andlinux on 2013-05-09
Newly made starter, the one that is working:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=VU+
Comment=
Exec=thunar smb://192.168.1.4/harddisk
Icon=
Path=
Terminal=false
StartupNotify=false

```


The old one that didn't worked when I upgraded:

```

[Desktop Entry]
Version=1.0
Type=Link
Name=Vu+
Comment=
Icon=gnome-fs-ftp
URL=thunar smb://192.168.1.4/harddisk

```

---

