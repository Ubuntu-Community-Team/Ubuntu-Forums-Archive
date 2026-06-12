---
title: "Gba emulator alternatives?"
date: 2013-08-10
forum: Emulators
---

### Post by cazz1 on 2013-08-10
Hello all, does anyone know of a good gba emulator for Ubuntu 12.4 besides vba and mednafen? Visual Boy Advance is too buggy, Mednafen is extremely useless, won't even start.

---

### Post by SweetAurora on 2013-08-10
Are you aware of the fact mednafen is command line driven? It dosen't "start up", it needs a command like 'mednafen /path/to/game/whatever.gba'
type 
```
mednafen --help
```
To get the list of commands you may be allowed to use with it.

---

### Post by cazz1 on 2013-08-10
Yes I'm aware, sorry that's what I meant. Won't run in command line.

---

### Post by LillyDragon on 2013-08-11
Have you tried VBA-M? It's a much better version of the emulator. A lot of the Windows version's advanced features are stripped out, but it runs like a dream and is very cooperative, unlike what you'll find in the Repos.

I have an SVN package, but this should be the same version number.

[http://www.ubuntuupdates.org/package/getdeb_games/precise/games/getdeb/vbam-gtk](http://www.ubuntuupdates.org/package/getdeb_games/precise/games/getdeb/vbam-gtk)

---

### Post by Sergio Benjamim on 2014-06-09
> **johnluke728 said:**
> Have you tried VBA-M? It's a much better version of the emulator. A lot of the Windows version's advanced features are stripped out, but it runs like a dream and is very cooperative, unlike what you'll find in the Repos.

I have an SVN package, but this should be the same version number.

[http://www.ubuntuupdates.org/package/getdeb_games/precise/games/getdeb/vbam-gtk](http://www.ubuntuupdates.org/package/getdeb_games/precise/games/getdeb/vbam-gtk)

Hey hello

Did you manage to fix the [loss of configuration]("http://sourceforge.net/p/vbam/bugs/147/") that vba-m suffers every time you quit the emulator [while you are running some rom] ? I saw that you have 1229 svn version.

I "fixed" it in my [branch]("https://code.launchpad.net/~sergio-br2/vbam/fixes"), and I made a PPA for it: [https://launchpad.net/~sergio-br2/+archive/vbam-trunk](https://launchpad.net/~sergio-br2/+archive/vbam-trunk). The truth is that i reverted 3 files to the commit 1227, related to sdl sound. This needs to be truly fixed yet.

---

