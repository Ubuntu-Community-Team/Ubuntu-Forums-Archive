---
title: "Quake3 Issues"
date: 2008-02-20
forum: Gaming &amp; Leisure
---

### Post by toasty_ghosty on 2008-02-20
I wanted to get a great game working in Ubuntu today so I went straight for quake3...have followed this 
[GUIDE]("http://www.errorforum.com/gaming-tutorials/623-installing-quake-iii-ubuntu.html")
guide and I keep getting an error:

:~/Games/quake3$ sudo ./linuxq3apoint-1.32b-3.x86.run
sudo: ./linuxq3apoint-1.32b-3.x86.run: command not found

Anyhelp?

---

### Post by DoktorSeven on 2008-02-20
1) type **ls** and make sure that executable is in the directory you're trying to run it from and that you're typing its name exactly (hint: use the TAB button to autocomplete filenames).

2) Make sure it is set executable (**chmod +x *(the filename here)*)**

---

### Post by toasty_ghosty on 2008-02-20
I did all that, it installed but when I try to run it I get this error:

ing@Linux:~/Games/quake3$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/theking/.q3a/baseq3
/usr/share/games/baseq3/pak8.pk3 (9 files)
/usr/share/games/baseq3/pak7.pk3 (4 files)
/usr/share/games/baseq3/pak6.pk3 (64 files)
/usr/share/games/baseq3/pak5.pk3 (7 files)
/usr/share/games/baseq3/pak4.pk3 (272 files)
/usr/share/games/baseq3/pak3.pk3 (4 files)
/usr/share/games/baseq3/pak2.pk3 (148 files)
/usr/share/games/baseq3/pak1.pk3 (26 files)
/usr/share/games/baseq3
./quake3.x86/baseq3

----------------------
534 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/theking/.q3a/demota
/usr/share/games/demota
./quake3.x86/demota

----------------------
534 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
rowing@Linux:~/Games/quake3$

---

### Post by toasty_ghosty on 2008-02-21
I finally got the game running. Everything seems fine. The only issue is the sound does not work. I thought this is because everything related to quake is only works with root access and root user did not have audio privileges but I changed this and it still does not work. Help?

---

### Post by disturbedite on 2008-02-21
i'd like to recommend ioquake3.  its basically a q3 development/bugfixes project to keep development going since ID software released the source code.

---

### Post by toasty_ghosty on 2008-02-24
Thank you. I found ioquake3 and now i can actually hear sound compared to quake3.

---

### Post by disturbedite on 2008-02-25
cool.  glad to help.
what i was trying to iterate tho, is that ioquake3 ***IS*** quake3.  its just that development has continued thanks to the community since the source was released.
in other words, the only difference is that ID software isn't developing it any more.
the community devs simply had to give it a different name to distinguish it from ID software.  (liability reasons?)

---

