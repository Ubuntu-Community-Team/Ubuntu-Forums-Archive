---
title: "Can't compile elite  : ("
date: 2006-06-26
forum: Gaming &amp; Leisure
---

### Post by jonboy99 on 2006-06-26
Hi, hopefully enough time has passed so people will have forgotten my last thread, 'can't compile elite 2'  :D

Anyway, am now trying to compile elite:the new kind.  This is the best reproduction of the original elite I have ever seen, having played the precompiled version on a windows machine.  

Am now trying to get it to work on linux, but having problems with an allegro library.

I got the source code from here:

[http://public.planetmirror.com/pub/elite/elite-tnk/](http://public.planetmirror.com/pub/elite/elite-tnk/)

(newkind.zip is the source code)

and a new makefile from here:

[http://www.geocities.com/dmalykhanov/utils/elite.html](http://www.geocities.com/dmalykhanov/utils/elite.html)

following a helpful post on a newsgroup.

I got errors with the makefile in the newkind.zip, so tried using the one from the geocities website, and renamed it from Makefile to makefile  (i'm getting the hang of this linux business slowly but surely  :D ).
However, i'm getting the following errors, which seem to imply problems with the allegro library - as far as i can tell the makefile is referencing a specific version of allegro (i've installed version 4.2.something and it's dev files via synaptic).
Do I need to install the older version of the library from the geocities website, and if so how do i install a .so file?  Or do I need to tweak the makefile somehow to reference the latest allegro version?  Or am I on the wrong track completely?

Cheers
Jon.

Errors when attempting a make command with the newkind.zip source and the makefile from the geocities site:

> jonboy99@xp24ubuntu:~$ cd Desktop
jonboy99@xp24ubuntu:~/Desktop$ cd "newkind folder"
jonboy99@xp24ubuntu:~/Desktop/newkind folder$ make
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  alg_gfx.c
alg_gfx.c: In function ‘gfx_display_text’:
alg_gfx.c:487: warning: ‘text_mode’ is deprecated (declared at /usr/include/alle gro/alcompat.h:153)
alg_gfx.c:488: warning: ‘textout’ is deprecated (declared at /usr/include/allegr o/alcompat.h:155)
alg_gfx.c: In function ‘gfx_display_colour_text’:
alg_gfx.c:494: warning: ‘text_mode’ is deprecated (declared at /usr/include/alle gro/alcompat.h:153)
alg_gfx.c:495: warning: ‘textout’ is deprecated (declared at /usr/include/allegr o/alcompat.h:155)
alg_gfx.c: In function ‘gfx_display_centre_text’:
alg_gfx.c:516: warning: ‘text_mode’ is deprecated (declared at /usr/include/alle gro/alcompat.h:153)
alg_gfx.c:517: warning: ‘textout_centre’ is deprecated (declared at /usr/include /allegro/alcompat.h:160)
alg_gfx.c: In function ‘gfx_display_pretty_text’:
alg_gfx.c:578: warning: ‘text_mode’ is deprecated (declared at /usr/include/alle gro/alcompat.h:153)
alg_gfx.c:579: warning: ‘textout’ is deprecated (declared at /usr/include/allegr o/alcompat.h:155)
alg_gfx.c: In function ‘gfx_set_clip_region’:
alg_gfx.c:592: warning: ‘set_clip’ is deprecated (declared at /usr/include/alleg ro/alcompat.h:205)
alg_gfx.c: In function ‘gfx_request_file’:
alg_gfx.c:766: warning: ‘file_select’ is deprecated (declared at /usr/include/al legro/alcompat.h:141)
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  alg_main.c
In file included from alg_main.c:48:
missions.h:7:7: warning: no newline at end of file
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  docked.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  elite.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  intro.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  planet.c
In file included from planet.c:28:
missions.h:7:7: warning: no newline at end of file
planet.c: In function ‘find_planet’:
planet.c:211: warning: ‘planet.f’ may be used uninitialized in this function
planet.c:211: warning: ‘planet.e’ may be used uninitialized in this function
planet.c:211: warning: ‘planet.d’ may be used uninitialized in this function
planet.c:211: warning: ‘planet.c’ may be used uninitialized in this function
planet.c:211: warning: ‘planet.b’ may be used uninitialized in this function
planet.c:211: warning: ‘planet.a’ may be used uninitialized in this function
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  shipdata.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  shipface.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  sound.c
sound.c:145:2: warning: no newline at end of file
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  space.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  swat.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  threed.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  vector.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  random.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  trade.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  options.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  stars.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  missions.c
In file included from missions.c:31:
missions.h:7:7: warning: no newline at end of file
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  pilot.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  file.c
gcc -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include -c  keyboard.c
gcc -o newkind.exe alg_gfx.o alg_main.o docked.o elite.o intro.o planet.o shipda ta.o shipface.o sound.o space.o swat.o threed.o vector.o random.o trade.o option s.o stars.o missions.o pilot.o file.o keyboard.o -Lallegro/lib -lalleg-3.9.37 -l alleg_unsharable
/usr/bin/ld: cannot find -lalleg-3.9.37
collect2: ld returned 1 exit status
make: *** [newkind.exe] Error 1
jonboy99@xp24ubuntu:~/Desktop/newkind folder$ make
gcc -o newkind.exe alg_gfx.o alg_main.o docked.o elite.o intro.o planet.o shipda ta.o shipface.o sound.o space.o swat.o threed.o vector.o random.o trade.o option s.o stars.o missions.o pilot.o file.o keyboard.o -Lallegro/lib -lalleg-3.9.37 -l alleg_unsharable
/usr/bin/ld: cannot find -lalleg-3.9.37
collect2: ld returned 1 exit status
make: *** [newkind.exe] Error 1


---

### Post by tonyr on 2006-06-26
This **elite:newkind** thing looks relatively old, so I would start by getting the 3.9.37
version and putting it in **allegro/lib**, wherever that is.  If there is a 3.9.37
version listed in Synaptic, you could try installing it that way, and forget the **geocities**
download. I haven't looked to see if it's in there.

You could also try changing the 3.9.37 library declaration in the Makefile(s) to 4.2-something,
(look in /usr/lib or /usr/lib/allegro to see what the version number is exactly)
but library evolution may have bypassed the code you have (i.e., it's not backward compatible).

---

### Post by jonboy99 on 2006-06-26
There isn't the older version in synaptic or on the allegro site.  Guess i'm going to have to fiddle with the makefile, which scares me  :(

---

### Post by jonboy99 on 2006-06-26
Hmm, looked in the makefile and can't see anything referencing a particular version of allegro so stuck.

[Edit] Hmm, yess there is..

---

### Post by tonyr on 2006-06-26
[QUOTE=jonboy99]There isn't the older version in synaptic or on the allegro site.  Guess i'm going to have to fiddle with the makefile, which scares me  :([/QUOTE]

If it were me, I'd go get the 3.9.37 version and try that first.

---

### Post by daveg on 2006-06-26
[QUOTE=jonboy99]Hmm, looked in the makefile and can't see anything referencing a particular version of allegro so stuck.

[Edit] Hmm, yess there is..[/QUOTE]

I'm guessing you found the reference to the specific version of allegro on line 7 of the Makefile?

```
#
# Makefile for Elite - The New Kind.
#

CC      =       gcc

LIBS    =       -Lallegro/lib **-lalleg-3.9.37** -lalleg_unsharable
CFLAGS  =       -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include
```

Should be:

```
#
# Makefile for Elite - The New Kind.
#

CC      =       gcc

LIBS    =       -Lallegro/lib **-lalleg** -lalleg_unsharable
CFLAGS  =       -mpentium -O2 -funroll-loops -Wall -DALLEGRO_STATICLINK -Iallegro/include
```

---

### Post by jonboy99 on 2006-06-27
Cheers.  I asked on the allegro forums (can't help thinking of my dad's old car whenever I say allegro  :D ) and they suggested replacing the line with

> 
`allegro-config --libs`

Which worked fine.  I the struggled until I released I needed to set the system path to the game directory (am now working on doing that with a bash script), and now game is working!  Albeit without sound, so just got to figure out how to get it to play the enclosed midi files.

The allegro guys were also pretty pissed at the makefile author for specifically referencing a version which was apparently a work in progress anyway  :)
Cheers.

---

### Post by jonboy99 on 2006-06-27
Hmm, ok - sound problems now.   Sound effects work fine, but these are just .wav files in the game directory.  The midi files don't play at all (eg background music).

When the game quits it leaves this error:

```
ALSA lib rawmidi_hw.c:231:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such file or directory
```

This is quite an old game, has the name of the linux midi device changed since then?  Anyway to rename it if so?  Can i mount it as something else?

---

### Post by daveg on 2006-06-27
[QUOTE=jonboy99]Cheers.  I asked on the allegro forums (can't help thinking of my dad's old car whenever I say allegro  :D ) and they suggested replacing the line with



Which worked fine.  I the struggled until I released I needed to set the system path to the game directory (am now working on doing that with a bash script), and now game is working!  Albeit without sound, so just got to figure out how to get it to play the enclosed midi files.

The allegro guys were also pretty pissed at the makefile author for specifically referencing a version which was apparently a work in progress anyway  :)
Cheers.[/QUOTE]
Ah, yes. Its coming back to me now. I found my Makefile, and for those two lines I actually had:

```
LIBS    =       $(shell allegro-config --libs)
CFLAGS  =       $(shell allegro-config --cflags)
```

---

### Post by jonboy99 on 2006-06-27
Did you have any luck with the midi playing when you compiled it?  (You aren't david gillies from the a.f.elite newsgroup are you?)

---

### Post by daveg on 2006-06-27
[QUOTE=jonboy99]Did you have any luck with the midi playing when you compiled it?  (You aren't david gillies from the a.f.elite newsgroup are you?)[/QUOTE]
No joy with MIDI sorry. I get the same error, but then again, I can't seem to play midi files on my system full stop, which may be the source of the error in the first place. Can you confirm that you can play midi files?

And yep, its me David :)

---

### Post by jonboy99 on 2006-06-27
Good to see you again  :mrgreen: 

No, can't play midi files either.  A quick search of the forums shows that it certainly was a problem, and there're how tos for older ubuntu versions.  I'd kind of hoped it had been fixed in dapper but I guess not.

I'll have to follow a how to like this one, haven't got around to it yet as elite TNK is the only prog where i've wanted midi playback.

[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

---

### Post by peterx14 on 2008-03-16
I thought I'd hijack this thread rather than create a new one! ;)

I'm trying to compile Elite - The New Kind and I think I have the same make file you had; I had to change it so it didn't specify a specific version of allegro. Anyway, it isn't complaining about much now, but it fails because it can't find alleg_unsharable. A quick google _seems_ to indicate that this has been removed from the debian package... but I could be wrong.

Here's what it's saying:
```
$ make -f Makefile 
gcc -o newkind.exe alg_gfx.o alg_main.o docked.o elite.o intro.o planet.o shipdata.o shipface.o sound.o space.o swat.o threed.o vector.o random.o trade.o options.o stars.o missions.o pilot.o file.o keyboard.o -Lallegro/lib -lalleg -lalleg_unsharable
/usr/bin/ld: cannot find -lalleg_unsharable
collect2: ld returned 1 exit status
make: *** [newkind.exe] Error 1
```

I should mention out at this point that I'm a noob as far as compiling anything goes, when stuff doesn't go to plan like this, I'm at a loss as to how to proceed. :confused:

Any help welcome!!

---

