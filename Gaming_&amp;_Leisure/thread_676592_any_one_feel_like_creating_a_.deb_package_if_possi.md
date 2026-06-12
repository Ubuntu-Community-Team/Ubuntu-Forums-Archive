---
title: "any one feel like creating a .deb package if possible"
date: 2008-01-23
forum: Gaming &amp; Leisure
---

### Post by pibb69173 on 2008-01-23
i need help creating a  deb pacage 4 the following game (or if u could make it and email it 2 me)


: rigs of rods

emal= 
thanx

---

### Post by Shazaam on 2008-01-24
Fun game. How far has it progressed?
Looks like the source is closed....

[http://www.rigsofrods.com/](http://www.rigsofrods.com/)

You COULD download the tarball for the game and use checkinstall to make yourself a .deb while installing.

.deb links....(some are old)
[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)
[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)
[http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html)
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)
[http://developer.assaydepot.com/?p=10](http://developer.assaydepot.com/?p=10)

---

### Post by loell on 2008-01-24
i suspect that the tarball is also binary? since it is closed source , so probably he can't use checkinstall.

---

### Post by Shazaam on 2008-01-24
> **loell said:**
> i suspect that the tarball is also binary? since it is closed source , so probably he can't use checkinstall.

Ahh, I stand corrected. Thank you.

---

### Post by DoktorSeven on 2008-01-24
Why do you need a .deb package?

Download RoR-0.33d-linux.tar.bz2 and put it in /tmp/.  Open a terminal.

```

cd /opt
sudo tar xfvj /tmp/RoR-0.33d-linux.tar.bz2
sudo mv RoR-0.33d-linux rigsofrods
sudo chmod -R 777 rigsofrods
gksudo gedit /usr/games/rigsofrods

```
Last command opens a text editor (blank).  Put this in:
```

#!/bin/bash
cd /opt/rigsofrods
./RoR $@

```
Save and close, then:
```

sudo chmod 755 /usr/games/rigsofrods

```

Now just make a desktop/launcher/start menu entry that points to /usr/games/rigsofrods

As noted, Debian packages of non-opensource games are a bit difficult to do.  This is not exactly easy, but at least trivial when you get the hang of it.

Edit: Oh, ok, also there's an extra dependency (libCg) that isn't in the Ubuntu repositories anyway.  To get this, go download Cg [here](http://developer.nvidia.com/object/cg-redistributable-binaries.html) (latest version), open with file-roller and go to /cg-redist-(version number here)/Linux/x86/gcc4/lib and extract the two files to your home directory.  Substitute x86_64 if you're running 64bit for the x86 part.

Then:
```
sudo cp ~/libCg*.so /opt/rigsofrods/
```

---

### Post by pibb69173 on 2008-01-24
i got it almost running but then i got this error:


Error: Unsupported depth 0... exiting

---

### Post by pibb69173 on 2008-01-24
ok i combined prts of diff packs but i need 1 more thing

i need libwx_gtk2_xrc-2.6.so.0

---

