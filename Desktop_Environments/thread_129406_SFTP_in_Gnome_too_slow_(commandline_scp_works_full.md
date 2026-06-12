---
title: "SFTP in Gnome too slow (commandline scp works full speed)"
date: 2006-02-13
forum: Desktop Environments
---

### Post by Oxygene on 2006-02-13
Hi,

I have a problem with my 5.10 Ubuntu installation. When I connect to a ssh ressource in Nautilus for example and copy files around, the full available bandwidth is _not_ used. I'm on a DSL line and should get ca. 125 KiB/sec downloads. The speed is varying somewhere between 70 and 100 KiB/sec instead. This is not limited to nautilus, it also happens with gftp (using ssh too). Therefore I believe that the problem must lie somewhere in the gnome-vfs. Unfortunately I'm just a user and not developer, so I have no insight in the architecture of the apps.

This is *always* reproducible. Using commandline sftp or scp always immediately uses the whole available bandwidth.

Do you have any ideas?

---

### Post by superm1 on 2006-02-13
I encounter this as well from within my apartment between two computers with 100Mb.  Transfers just crawl in gnome and gftp.  This is why I resorted to learning scp.  I guess scp isn't really that hard to use, but still i'd prefer to be able to just "Connect to server" instead of having to ssh in, see what the exact names of the files are, go back and scp, and such.

---

### Post by juancnuno on 2006-02-13
This might be unrelated, but I connect to a secure DAV server with Nautilus, and browsing my files is slow.  I guess it's better than using the web interface, but I wish Nautilus was more responsive.

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=superm1]I encounter this as well from within my apartment between two computers with 100Mb.  Transfers just crawl in gnome and gftp.  This is why I resorted to learning scp.  I guess scp isn't really that hard to use, but still i'd prefer to be able to just "Connect to server" instead of having to ssh in, see what the exact names of the files are, go back and scp, and such.[/QUOTE]
Can you just use command line sftp?  That should be part of your ssh install, and it should let you transfer files over ssh interactively.

---

### Post by Oxygene on 2006-03-03
Of course, using scp and sftp solves the speed problem. Knowing how to work without a GUI is important, but if we want to have a GUI, this most often implies that we want to have a *functional* GUI that is not only as performant as the equivalent cli-tools but also easier and faster to use.

ssh/scp support in KDE works well, so that I have used konqueror instead. It would be a pity if gnome/nautilus would lose its users, just because nobody seems to address this bug (I have found a bug in the gnome bugzilla, but nobody from the developers answers: [http://bugzilla.gnome.org/show_bug.cgi?id=155872](http://bugzilla.gnome.org/show_bug.cgi?id=155872)) :(

---

