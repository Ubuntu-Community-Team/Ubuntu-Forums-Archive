---
title: "How can i see the Frames per Second of a Game i am running?"
date: 2011-12-16
forum: Gaming &amp; Leisure
---

### Post by Basher101 on 2011-12-16
just as the title says, how can i view the fps of a game i am currently running? I searched google and the forums but get nothing...

The game i want to view the frames on is Heroes of Newerth so i can compare my GTX 570 performance in Ubuntu with Windows. 

thanks in advance

---

### Post by Arthur_D on 2011-12-16
I think that'll be game-specific. Check the options menu and configuration file(s).

---

### Post by Basher101 on 2011-12-16
> **Arthur_D said:**
> I think that'll be game-specific. Check the options menu and configuration file(s).

I am sure some games have something in-built to show frames. What i want is a program or command that shows the frames on the screen (like Fraps does for windows) for games that do NOT have those in-built fps features (like Heroes of Newerth which i want to test..)

---

### Post by WienerWuerstel on 2011-12-16
[Mumble]("http://mumble.sourceforge.net/") with the Overlay should do the trick. To get Mumble to show the FPS you need it to start Mumble first and then set the Overlay to show the FPS and after that you start your Game via the Terminal with a command like this ```
mumble-overlay game
```

*Replace game with the Name of the Game that you want to start

---

### Post by Basher101 on 2011-12-17
thanks i will try it

---

### Post by Basher101 on 2011-12-22
i tried mubmle but i get this error
```
stiv@Armageddon:~$ mumble-overlay /home/stiv/HoN/hon.sh
set
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
warning: The VAD has been replaced by a hack pending a complete rewrite
./hon-x86_64: symbol lookup error: /usr/lib/mumble/libmumble.so.1: undefined symbol: glXGetCurrentContext

``` is there any other program that can show the FPS?

p.s. sorry that i reply that late...had alot to do with school and such..

---

### Post by WienerWuerstel on 2011-12-23
Is Mumble running in the background and how did you install Mumble?

Maybe it could also be a missing lib and that's no reason to give up already.

---

