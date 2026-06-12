---
title: "Quake 3 problems?"
date: 2006-09-16
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2006-09-16
I can't seem to get Quake 3 to run. I've tried installing it (seems maybe twice since I've got it twice in the "Other" menu..)

When I try to launch it from terminal I get the following.

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/stephen/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
534 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/stephen/.q3a/demota
/usr/local/games/quake3/demota
./quake3.x86/demota

----------------------
534 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg

The Pak0 comes straight from the CD and I follow a set up guide perfectly, so I have no idea :(

---

### Post by Ziox on 2006-09-16
it reminds me of a problem I had when I tried a torrent of Quake 3...apparently the torrent didn't work for Linux :(.  Are you sure you are using a legitimate CD?

---

### Post by Anduu on 2006-09-17
If you look at the lines where it parses the pak files pak0.pk3 is missing.

Try copying it over again.

---

### Post by slyvren on 2006-10-09
Check your permissions on the base0.pk3, I had to give mine '777' and also had to change it to a lowercase filename.

---

