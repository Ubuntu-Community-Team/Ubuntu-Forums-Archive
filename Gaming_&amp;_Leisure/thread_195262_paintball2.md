---
title: "paintball2"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by RotoGrip on 2006-06-12
Anyone try this game ou tin Dapper yet? Runs great but i get no sound. I know..what a surprise;)  heres my output.

------- sound initialization -------
Cmd_AddCommand: play already defined
Cmd_AddCommand: stopsound already defined
Cmd_AddCommand: soundlist already defined
Cmd_AddCommand: soundinfo already defined
Initializing Linux sound.
/dev/dsp: Success
SNDDMA_Init: Could not mmap /dev/dsp.

---

### Post by charlieg on 2006-06-12
In case you were wondering, he means this game:
[http://digitalpaint.planetquake.gamespy.com/](http://digitalpaint.planetquake.gamespy.com/)

---

### Post by chadk on 2006-06-13
Well you get further than I do.
```

[/home/chad/paintball2]$ ./paintball2
Paintball 2 -- Version 3.21+r0.16
execing configs/default.cfg
Console initialized.

------- sound initialization -------
Initializing Linux sound.
sound sampling rate: 11025
------------------------------------
------- Loading ref_glx.so -------
LoadLibrary("./ref_glx.so")
ref_gl version: PB2GL 0.16
./libGL.so: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "libGL.so"
recursive shutdown
Error: Couldn't load gl refresh!
```

---

### Post by RotoGrip on 2006-06-13
Chadk

 Follow this link, i had this problem as well. It works.

[http://dpball.com/forums/index.php?topic=2406.0](http://dpball.com/forums/index.php?topic=2406.0)

---

### Post by em3raldxiii on 2006-06-26
[QUOTE=RotoGrip]Chadk

 Follow this link, i had this problem as well. It works.

[http://dpball.com/forums/index.php?topic=2406.0](http://dpball.com/forums/index.php?topic=2406.0)[/QUOTE]

This link worked for me to some degree, but I had some problems after starting the game ... here is what I posted in the paintball forum:

The game boots to menu as per usual, but my mouse is rammed to the top of the window.  I 'CAN' move it down, but as soon as I touch the mouse it creeps rather quickly to the top of the screen.  Very strange.

I can navigate the menus using the arrows, and I can adjust all the settings just fine that way.

If I go to the JOIN game, however, as soon as I try to navigate around with the arrows, the game crashes and closes with no error messages.

If I start my OWN game, it seems to work, but I am perpetually staring at the ceiling.  If I pull down, I can look down momentarily, but it always creeps up to the ceiling again.

And I only moved about for about 20 seconds before quitting, but my FPS looks okay.

Any thoughts?

Also note my sound KINDA works.  The sound effects ARE there, but they are patchy ... cut in and out.

Em

---

### Post by eldragon on 2006-10-31
this is what i found out:
starting from clicking paintball2 through nautilus gives you this sort of behavior, if you run it throught a terminal, it works ok. without sound

running edgy eft.

---

### Post by em3raldxiii on 2006-10-31
Thanks, I'll give it a try.  And if something suddenly starts working correctly I'll let you know.  Worst case scenario and I will try it with WINE.

---

### Post by PhrankDaChickenGeek on 2006-11-04
Mine keeps on randomly crashing. Anyone else with this problem?

---

### Post by PhrankDaChickenGeek on 2006-11-04
I was using alpha 016, but alpha 014 seems more stable on Linux. I haven't had 014 crash yet

---

