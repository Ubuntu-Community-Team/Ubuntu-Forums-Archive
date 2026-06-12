---
title: "XMMS Skins"
date: 2006-01-08
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-01-08
OK - I have XMMS installed and working fine however I can't seem to load or find new browser skins.

```
stricom@ubuntu:~$ sudo apt-cache search xmms-skins
xmms-skins - Skins for XMMS
stricom@ubuntu:~$ sudo apt-get install xmms-skins
Reading package lists... Done
Building dependency tree... Done
xmms-skins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

As you can see from the command above, it appears I have installed and have the latest skins for XMMS but when I open XMMS, and try and change the skin, I can't find any...:confused: 

[IMG]http://img267.imageshack.us/img267/7440/xmms3ff.png[/IMG]

---

### Post by schilcha on 2006-01-08
You need to "Add directory". xmms-skins will not install files in you home. 
Add "/usr/share/xmms/Skins"

---

### Post by myke on 2006-01-08
Go here:  [Gnome-look.org]("http://www.gnome-look.org/")

You can download xmms skins via the menu on the left of the main page.   Create a folder somewhere like in home and simply add that directory via the menu in the skins browser like in the window you printed below.  All the skins you download will be read that way directly from the tarball so you won't have to decompress them.

You can also use beep, a derivative of xmms, and you'd simply add decompressed skin folders to the folders called 'skins' in /home/usr/share/bmp.

---

### Post by myke on 2006-01-08
BTW -- the directory in the screen shot /home/stricom/.xmms/skins is a hidden folder.  You can also drop a bunch of downloaded skins in there manually via tarball but you'll have to go to the view dropdown menu and add hidden files to be viewed.  It's rather a pain that way so I just use bmp.   XMMS will read tarballs but the skins have to be extracted to their individual folkder when you use beep media player (bmp).  I don't know why.

---

### Post by CarlosinFL on 2006-01-08
[QUOTE=schilcha]You need to "Add directory". xmms-skins will not install files in you home. 
Add "/usr/share/xmms/Skins"[/QUOTE]

I added the directory and it worked fine.

Thanks!

---

