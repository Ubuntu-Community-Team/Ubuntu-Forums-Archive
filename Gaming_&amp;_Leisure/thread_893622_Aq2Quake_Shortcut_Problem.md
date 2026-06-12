---
title: "Aq2/Quake Shortcut Problem"
date: 2008-08-18
forum: Gaming &amp; Leisure
---

### Post by formigo on 2008-08-18
Hi ppl
I'm new at Ubuntu.
My problem is very simple. I compiled the client AprQ2 to play Action Quake 2 in Ubuntu (Quake2 Mod). The game works fine, but I don't know why, when I make a shortcut or a symlink to the file aq2 in my Desktop, he doesn't work. The only way to start the game is executing aq2 from the local folder. Can somebody help me?

Thanks ;)

---

### Post by Brebs on 2008-08-18
This is probably because the executable looks for the data files **relative** to the current directory, rather than as absolute paths.

Ideally there would be a compilation option to specify the absolute path at compile-time, e.g. with [kmquake2](http://fedoraforum.org/forum/showthread.php?p=1053934):
```
make DATADIR=/usr/share/wherever BUILD_DATADIR=YES
```

---

### Post by formigo on 2008-08-18
Grrr, anyone knows what librarie I need for the compiling error I got above?

I think it's something about SDL Sound refered to MP3 Playback, since AprQ2 have support for Winamp on Windows. Anyone can help me?> [QUOTE][/QUOTE]

---

### Post by Brebs on 2008-08-19
Compile [aprq2](http://www.quakeunity.com/file=2661) with e.g.:
```
make \
	BUILD_XMMS=NO \
	BUILD_OPENAL=NO \
	BUILD_HTTP=YES \
	BUILD_SDLSOUND=YES \
	BUILD_SDL=YES
```

---

### Post by formigo on 2008-08-19
Nop, with the make command that Brebs sayed still can't open AprQ2 by a shorcut. It opens and closes the window very quickly.

I have another problem too. Many files in Aq2 are with uppercase, and since Linux/Ubuntu files are case sensitivity, AprQ2 doesn't load a lot of files. Is there any command to put the files in the folder case insensitivity? Or I have to rename it all to lowercase?

---

### Post by Brebs on 2008-08-19
If you're using a shortcut then you need to set the current directory, as I stated earlier. This can be done using a "wrapper script", e.g.:

/usr/bin/run-game-properly
```
#!/bin/sh

cd /usr/share/wherever
./game-executable "$@"
```
That "$@" are the rest of the command-line parameters that may have been passed.

---

### Post by formigo on 2008-08-19
Yeah, with the script worked out. Thanks a lot Brebs.
How about putting all the files in lowercase? Don't know anything about it?

:)

---

### Post by Brebs on 2008-08-19
There's [several ways](http://webxadmin.free.fr/article/shell-rename-all-files-in-subdirectories-to-lowe-135.php) to [rename files to lower-case](http://gentoo-wiki.com/TIP_lowercase_files_and_directories).

Exactly which sources have you used for Action Quake 2? The one I linked to fails to run in Fedora 9, with error message:

> LoadLibrary (/usr/lib64/aprq2/baseq2/gamex86_64.so): undefined symbol: Com_Error

Which I've been unable to fix so far :(

---

### Post by formigo on 2008-08-19
[http://maniac.aq2world.com/apr/aprq2_v1.211-src.zip](http://maniac.aq2world.com/apr/aprq2_v1.211-src.zip)

---

### Post by Brebs on 2008-08-19
Aha, that's a later version but unfortunately still the LoadLibrary problem in Fedora 9 - I bet it's an issue with using gcc 4.3 rather than the 4.2 in Ubuntu Hardy, so Intrepid (which [will use 4.3](http://packages.ubuntu.com/intrepid/gcc)) will have the same problem.

Let's see if my C programming talent improves :)

---

### Post by formigo on 2008-08-19
It's strange, because the "Com_Error" appears sometimes in quake 2 console, but I think your compiling the x64 version, and I compiled the x86 version, no?

---

### Post by Brebs on 2008-08-19
OK, it's [working now](http://forums.aq2world.com/viewtopic.php?t=3323) :)  On 64-bit too.

Although my patches to use /usr/share and /usr/lib64 are not 100% - the patching of sv-ccmds.c is incomplete.

Anyway, see [aprq2 files](ftp://brebs.me.uk/fedora/9/) - the .src.rpm should be openable in file-roller, and the .spec file shows the build commands.

---

### Post by formigo on 2008-09-03
Krename solves the problem (lowercase files), but it's too damm slow. :D
And it's stupid, but using Wine, the AprQ2.exe run's more faster (fps) than using the compiled version.

---

