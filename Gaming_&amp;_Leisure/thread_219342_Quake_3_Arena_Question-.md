---
title: "Quake 3 Arena Question-"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by andy- on 2006-07-19
Hi again, I'm getting this error when running Quake 3 Arena:

[I]andy@home:~$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/andy/.q3a/baseq3
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
/home/andy/.q3a/demota
/usr/local/games/quake3/demota
./quake3.x86/demota

----------------------
534 files in pk3 files
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg
andy@home:~$[/I]

Do I have to manually create a *.cfg first? not sure what's going on. 
Also it says "Running in restricted demo mode." I have full version. :( 

Thanks for the help. :-|

---

### Post by goobers on 2006-07-19
just checking, did you copy the pak0.pk3 file from your quake 3 cd before running?

---

### Post by andy- on 2006-07-19
I just sudo sh the *.run file. I was hoping it did everything on its own.

---

### Post by goobers on 2006-07-19
it appears that it hasn't. try copying the pak0.pk3 file from your cd to /usr/local/games/quake3/baseq3/

---

### Post by vem0m on 2006-07-19
yea u gotta copy that file of ur cd to the /usr/local/games/quake3/baseq3/ directory

---

### Post by andy- on 2006-07-19
Great, thank you, that did it.

---

### Post by goobers on 2006-07-19
No probs :)

---

### Post by vem0m on 2006-07-19
np :) enjoy the game :)

---

### Post by Qwerty_ on 2006-07-20
> **goobers said:**
> it appears that it hasn't. try copying the pak0.pk3 file from your cd to /usr/local/games/quake3/baseq3/

How do i copy my files there i does not let me copy to that dir. do i have to be a su?

---

### Post by vem0m on 2006-07-20
yes u do

---

### Post by crane on 2006-07-20
should be something like:
sudo cp /media/cdrom/Quake3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3/pak0.pk3

---

### Post by andy- on 2006-07-25
Just cd into your Quake3 CD 'baseq3' directory where the pak0.pk3 is located. And just do: 

[COLOR="Red"]andy@home:/media/cdrom0/Quake3/baseq3$ sudo cp -r pak0.pk3 /usr/local/games/quake3/baseq3/[/COLOR]

---

