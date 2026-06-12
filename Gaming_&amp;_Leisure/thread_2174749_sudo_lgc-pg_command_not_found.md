---
title: "sudo: lgc-pg: command not found"
date: 2013-09-16
forum: Gaming &amp; Leisure
---

### Post by ikki_72 on 2013-09-16
after i installed lgeneral and put extracted pg-data inside ~/Downloads

i ran

```
$ sudo lgc-pg -s Downloads/pg-data/ -d /usr/share/games/lgeneral/
sudo: lgc-pg: command not found
```

had anyone successfully done played lgeneral on ubuntu 13.04?

---

### Post by MikeCyber on 2013-09-16
it's not in any /bin directory. Hence cd to where it is and execute: ./lgc-pg

---

### Post by ikki_72 on 2013-09-16
so i tried invoking that binary directly and nations directory could not be found despite purging and reinstall of lgeneral

```
$ sudo /usr/games/lgc-pg -s Downloads/pg-data/ -d /usr/share/games/lgeneral
LGeneral Converter for Panzer General (DOS version) v1.2.3
Copyright 2002-2012 Michael Speck
Released under GNU GPL
---
Settings:
  Source: Downloads/pg-data/
  Destination: /usr/share/games/lgeneral
  Target: pg
  Full Campaign
  Use Individual Palettes
  Apply PG unit modifications
Converting:
Nation database...
/usr/share/games/lgeneral/nations/pg.ndb: access denied

$ ls /usr/share/games/lgeneral/
campaigns  convdata  gfx  sounds  themes
```

---

### Post by MikeCyber on 2013-09-16
read...
probably it needs a 
chmod -R 777 
/usr/share/games/lgeneral/nations/pg.ndb

use sudo only when needed!

---

### Post by ikki_72 on 2013-09-16
thanks for that info man...unfortunately

```
$ ls -l /usr/share/games/
total 28
drwxr-xr-x 4 root root 4096 Sep   3 16:17 brutalchess
drwxr-xr-x 2 root root 4096 Sep   3 16:14 fruit
drwxr-xr-x 3 root root 4096 Sep  16 12:04 game-data-packager
drwxr-xr-x 7 root root 4096 Sep   3 19:26 glGo
drwxr-xr-x 2 root root 4096 Sep   3 16:19 gnuchess
drwxrwxrwx 7 root root 4096 Sep  16 16:10 lgeneral
drwxr-xr-x 4 root root 4096 Sep  12 15:22 xgalaga

$ ls -l /usr/share/games/lgeneral/total 20
drwxrwxrwx 2 root root 4096 Sep  16 16:10 campaigns
drwxrwxrwx 2 root root 4096 Sep  16 12:04 convdata
drwxrwxrwx 2 root root 4096 Sep  16 16:10 gfx
drwxrwxrwx 2 root root 4096 Feb  21  2013 sounds
drwxrwxrwx 3 root root 4096 Sep  16 16:10 themes

$ /usr/games/lgc-pg -s Downloads/pg-data/ -d /usr/share/games/lgeneral
LGeneral Converter for Panzer General (DOS version) v1.2.3
Copyright 2002-2012 Michael Speck
Released under GNU GPL
---
Settings:
  Source: Downloads/pg-data/
  Destination: /usr/share/games/lgeneral
  Target: pg
  Full Campaign
  Use Individual Palettes
  Apply PG unit modifications
Converting:
Nation database...
/usr/share/games/lgeneral/nations/pg.ndb: access denied
```

---

### Post by Am Elder on 2013-09-16
I just tried building and installing it from source, without touching any directories outside of my home directory, following the directions in the READMEs and I still got a permission denied error.  Looks like a problem with the conversion script?

The sourceforge page points to inactive forums and a mailing list without any mail, so I recommend contacting the developer directly using the info on the LGames site: [http://lgames.sourceforge.net/contact.php](http://lgames.sourceforge.net/contact.php)

---

### Post by hironiemus on 2013-11-17
I just came across the same problem. If you look at the folder you will see that the file in question does not exist. Neither does the parent folder. 
The solution is simple: The converter script doesn’t seem to create new directories, so you need to create them by hand. 

Assuming you’re in /usr/games/lgeneral the following should get you sorted: (adjust source folder accordingly)

```

sudo mkdir -p nations gfx/flags units gfx/units maps gfx/terrain/pg scenarios/pg
sudo /usr/games/lgc-pg -s /media/PG_V1_2/dat -d /usr/share/games/lgeneral
```

[IMG]http://img46.imageshack.us/img46/7466/u7tk.png[/IMG]

Enjoy!

---

