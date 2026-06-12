---
title: "How do I compile wolf3D?????"
date: 2007-10-02
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2007-10-02
How do I compile Wolfenstein 3D natively?

I found native files [here]("http://www.linux-gamers.net/modules/wfdownloads/singlefile.php?cid=36&lid=106") but I can't get it to compile with Ubuntu.I get a bunch of code followed by this error line on the Terminal:

make: *** [sd_null.o] Error 1

Has anyone else manged to get this game to compile?Am I missing dependencies or is the game just so old that its not going to work with Ubuntu?Yes I am aware that wolf3D works with Dosbox.

---

### Post by DoktorSeven on 2007-10-02
After installing the requirement of **libsdl1.2-dev** I found that it generated this error that lead to that final line you pasted (note: when compiling and pasting the error, you need to go back and find the actual error message(s) that are printed -- you can ignore lines that say "warning", but include all "error" lines):

sd_null.c:5: error: conflicting types for ‘MusicMode’
sd_comm.h:19: error: previous declaration of ‘MusicMode’ was here

Sure enough, in sd_comm.h and sd_null.c the value of MusicMode was defined two ways.  Edit sd_comm.h and look for:

extern	SMMode		MusicMode;

Change it to:

extern	SDMode		MusicMode;

and it should compile.

---

### Post by Dark Aspect on 2007-10-02
Thanks for the reply but now it seems I have a new error: (its the whole terminal output now)

> gcc -o sdlwolf3d objs.o misc.o id_ca.o id_vh.o id_us.o wl_act1.o wl_act2.o wl_act3.o wl_agent.o wl_game.o wl_inter.o wl_menu.o wl_play.o wl_state.o wl_text.o wl_main.o wl_debug.o vi_comm.o sd_comm.o sd_null.o wl_draw.o vi_sdl.o -lm `sdl-config --libs` -L/usr/X11R6/lib -lX11 -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make: *** [sdlwolf3d] Error 1


I think it wants me to install SDL video from that last line of code and last time I did that I bricked Ubuntu 7.04........Thanks for the help so far any ideas for the new error or should I just stick with Dosbox?

---

