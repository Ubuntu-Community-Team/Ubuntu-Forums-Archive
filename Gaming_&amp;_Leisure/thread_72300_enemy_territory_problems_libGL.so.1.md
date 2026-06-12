---
title: "enemy territory problems: libGL.so.1"
date: 2005-10-05
forum: Gaming &amp; Leisure
---

### Post by nrayever on 2005-10-05
maybe this is a repeated thread. but i can't find the solution at the forum. yesterday, i installed enemy territory 2.60 and when i tried to run it i got this:

```
~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/nrayever/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...


```

those any one knows that's going on?? any posible solution to this problem??? i googled a bit but no answer. and here at the forums, i looked a bit and no exact match to this problem. i hope someone could help me.

nrayever

---

### Post by mlomker on 2005-10-05
I found some [references]("http://www.ubuntuforums.org/showthread.php?t=19843&page=2") to this error when running amd64.  Are you on 32-bit?

---

### Post by nrayever on 2005-10-05
i'm a proud amd64 user!!:D :D :D  is this a common problem in 64-bits computers???

---

### Post by mlomker on 2005-10-05
[QUOTE=nrayever]i'm a proud amd64 user!!:D :D :D  is this a common problem in 64-bits computers???[/QUOTE]

It is when you're running 32-bit programs on a 64-bit machine.  There are instructions in there that should help you out, but if you're serious about games then you might want to install the 32-bit Ubuntu instead.

---

### Post by nrayever on 2005-10-05
i have ut2004, and it runs smoothly on my amd64. right know i'm giving a try with one of the several solutions that are avaliable on the thread you told me. hope one of those works.

is gaming a privilegue for 32-bits users??? i hope not :( :(

---

### Post by nrayever on 2005-10-05
no luck!!! maybe gaming is a privilege for 32-bits users......... :???: :???: :???: :???:

---

### Post by Zimmer on 2005-10-06
You don't say what Video Card you are using..and if 3d acceleration is actually working (which ,according to many threads out there in the universe ,is the usual cause of error message  signal 11  forcing it to exit).

Have you been here ?
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

I have experienced both  ATI driver problems AND sound problems in getting ET to work , but the problems are usually overcome...essential, if one is to stay with Linux  :)
(I switched to Ubuntu from Fedora core 2 after a kernel upgrade screwed ET. It looked like a graphics problem and I even went to the lengths of swapping  graphics cards for an Nvidia one and re installing  Ubuntu to set up the different drivers in an effort to solve it.Then I discovered it was a sound problem .)
 You may find that you solve the GL 3D support problem and it will then stall on loading the Sound modules ...there are solutions for that, so do not despair......

Good Luck

Zimmer

---

