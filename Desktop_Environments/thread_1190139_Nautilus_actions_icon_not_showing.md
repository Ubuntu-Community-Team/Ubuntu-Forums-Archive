---
title: "Nautilus actions icon not showing"
date: 2009-06-17
forum: Desktop Environments
---

### Post by nikosm on 2009-06-17
Hello everybody,

I have added a nautilus action to the context menu and added an icon for it, but it is not showing (see screenshot).

About the icon:
```
identify flickr-icon.png 
flickr-icon.png PNG 256x256 256x256+0+0 8-bit DirectClass 23.8kb 
```

I remember this happening with old distributions as well. I find it odd that the icon is showing fine in the nautilus actions configuration window (resized and everything). There is some transparency in the png, but converting to jpg didn't help.

Thanks for any ideas,
Nikos

[COLOR="Blue"]Edit: attached icon.[/COLOR]

---

### Post by valex on 2009-06-17
please attach that icon also.

---

### Post by nikosm on 2009-06-17
Thanks for the fast reply. Icon attached above.

Nikos

---

### Post by valex on 2009-06-17
omg..! I got three bugs.!!!

[https://bugs.edge.launchpad.net/ubuntu/+source/google-gadgets/+bug/326496](https://bugs.edge.launchpad.net/ubuntu/+source/google-gadgets/+bug/326496)
(old one)
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/388594](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/388594)
new bug. as i think.
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/388591](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/388591)
not a bug. invalid.


Stucked my nautilus file browser. and no icons in desktop

I think this icon is too big. 
try resize icon using gimp or other graphical software.

---

### Post by nikosm on 2009-06-17
> **valex said:**
> 
I think this icon is too big. 
try resize icon using gimp or other graphical software.

That didn't work. I tried
16x16
18x18
22x22
24x24
32x32
48x48
64x64

none of them worked (I quit and restarted nautilus after each change). Even chosing a different png icon from /usr/share/pixmaps/gnome-news.png didn't show up...

This is quite weird. Can somebody suggest a png icon that will work for sure?

Thanks,
Nikos

[COLOR="Blue"]Edit: maybe this is relevant: starting nautilus from the bash outputs an error (that seems unrelated to me, without really knowing what it means:
```
$ nautilus -q; nautilus
Initializing nautilus-open-terminal extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4706): WARNING **: Unable to add monitor: Not supported
```[/COLOR]

---

