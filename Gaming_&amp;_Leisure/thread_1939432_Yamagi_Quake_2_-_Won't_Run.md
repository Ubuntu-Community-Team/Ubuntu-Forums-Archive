---
title: "Yamagi Quake 2 - Won't Run"
date: 2012-03-11
forum: Gaming &amp; Leisure
---

### Post by ArthurPeale on 2012-03-11
I'm completely perplexed.  What I would think should be a simple
installation just isn't working.

I've installed 4.03 as per the instructions on the Yamagi site.  Downloading
the Windows last point release, deleting the files listed that should
be deleted, installing the 64 bit .deb.  When I attempt to run the
quake2 binary, I get this:

arthur@Shadow:/usr/lib/games/yamagi-quake2$ ./quake2

Yamagi Quake II v4.03
=====================

Using /usr/share/games/quake2//baseq2/ to fetch paks
Added packfile '/usr/share/games/quake2//baseq2/pak0.pak' (3307 files).
Added packfile '/usr/share/games/quake2//baseq2/pak1.pak' (279 files).
Added packfile '/usr/share/games/quake2//baseq2/pak2.pak' (2 files).
Added packfile '/usr/share/games/quake2//baseq2/q2e_extras.pk2' (106 files).
Added packfile '/usr/share/games/quake2//baseq2/q2e_pak0.pk2' (594 files).
Added packfile '/usr/share/games/quake2//baseq2/q2e_enhanced_hud.pk2' (114 files).
Using '/home/arthur/.yq2/baseq2' for writing.
execing default.cfg
couldn't exec yq2.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
Starting SDL audio callback.
SDL audio driver is "pulse".
SDL audio initialized.
sound sampling rate: 11025
Starting Ogg Vorbis.
Ogg Vorbis not initializing.
------------------------------------

----- refresher initialization -----
LoadLibrary("./ref_gl.so")
Input initialized.
Refresh: Yamagi Quake II OpenGL Refresher
./opengl32: cannot open shared object file: No such file or directory
ref_gl::R_Init() - could not load "opengl32"
Input shut down.
CDAudio_Init: No CD in drive.
CDAudio_Init: CD contains no audio tracks.
D Audio Initialized.
Unknown command "d1"
==== Yamagi Quake II Initialized ====

*************************************

...and there it sits.  You can see the error, above, but I'm not sure
how to correct it.  I'm running a fairly stock Ubuntu 10.10 with an
ATI video card.

If I create a quake directory under my home directory, with all the necessary files, and run the executable, it goes a bit further, but segfaults:

Product:      Yamagi Quake II
Version:      4.03
Plattform:    Linux
Architecture: amd64
Signal:       11

Backtrace:
  ./quake2() [0x44355c]
  ./quake2() [0x443670]
  /lib/libc.so.6(+0x33c20) [0x7feecaa3ac20]

Segmentation fault

Any pointers?

---

### Post by ArthurPeale on 2012-03-12
Got it.  It was referring to a line in config.cfg  in baseq2.  I hadn't seen it before.  Once I removed the reference to opengl32, it came up.  I can't get the resolution that I'd like, but it's playable, at lease.

---

### Post by madjr on 2012-03-12
looks good, will try it (re-living old memories :))

[http://www.youtube.com/watch?v=x0JMyO_TnHs](http://www.youtube.com/watch?v=x0JMyO_TnHs)

---

### Post by Rodney9 on 2012-03-13
I have followed the instructions, but i get the following error -

```
/usr/lib/games/yamagi-quake2$ ./quake2

Yamagi Quake II v4.03
=====================

Using /usr/share/games/quake2//baseq2/ to fetch paks
Using '/home/rodney/.yq2/baseq2' for writing.
couldn't exec default.cfg
couldn't exec yq2.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
Starting SDL audio callback.
SDL audio driver is "alsa".
SDL audio initialized.
sound sampling rate: 44100
Starting Ogg Vorbis.
Ogg Vorbis not initializing.
------------------------------------

----- refresher initialization -----
LoadLibrary("./ref_gl.so")
Input initialized.
Refresh: Yamagi Quake II OpenGL Refresher
Closing SDL audio device...
SDL audio device shut down.
recursive shutdown
Error: Couldn't load pics/colormap.pcx
 
```

I have googled ```
Error: Couldn't load pics/colormap.pcx
```
and tried re copying the pak files, copied the entire cd , changed permissions, still get the same error.

Can anyone help please ?

Rodney

---

### Post by winh8r on 2012-03-13
I know this is for a different game, but there is mention of a script in this old thread that you might be able to make use of:

[http://ubuntuforums.org/archive/index.php/t-938518.html]("http://ubuntuforums.org/archive/index.php/t-938518.html")

Seems to cure the same error for another game.

Hope it helps.

---

### Post by Rodney9 on 2012-03-13
> **winh8r said:**
> I know this is for a different game, but there is mention of a script in this old thread that you might be able to make use of:

[http://ubuntuforums.org/archive/index.php/t-938518.html]("http://ubuntuforums.org/archive/index.php/t-938518.html")

Seems to cure the same error for another game.

Hope it helps.

Afraid not.

I shall delete everyhing and try again.

Rodney

---

### Post by Rodney9 on 2012-03-13
Deleted and re-installed, now all working, except I can not save games.

Rodney

---

### Post by Rodney9 on 2012-03-15
I worked it out, you have to run Yamagi Quake 2 as root to be able to save.

Are there any other/better Quake 2 versions/mods for single play ?

Rodney

---

### Post by Brebs on 2012-03-16
> **Rodney9 said:**
> as root
No, that's wrong.

I'm not sure if yamagi needs the data files installed somewhere in your home dir, and be run from there.

But *NO* game should be run as the root user. [Example of why it's so bad](http://insecure.org/sploits/quake.backdoor.html).

> Are there any other/better Quake 2 versions/mods for single play ?
E.g. [1492](http://www.markshan.com/thesinraven/1492_anno_domini_mod.htm).

---

### Post by Rodney9 on 2012-03-17
> **Brebs said:**
> No, that's wrong.

I'm not sure if yamagi needs the data files installed somewhere in your home dir, and be run from there.

But *NO* game should be run as the root user. [Example of why it's so bad](http://insecure.org/sploits/quake.backdoor.html).


E.g. [1492](http://www.markshan.com/thesinraven/1492_anno_domini_mod.htm).

Thank You

I copied the entire directory from usr/lib/games into my home and now it works, so Thanks again.

Rodney

---

### Post by DaveBilling on 2012-03-23
I got it to run no problems, the only problem for me is that the game stutters horribly.  Choppy sound and choppy video is all I get :(

---

### Post by sulyi on 2012-03-25
This works fine for me.

Though I've tried the one with [loki installer]("http://www.liflg.org/?catid=6&gameid=55") and that was very laggy. Maybe you would have better luck with that. Also check libsdl packages, and be sure that the package for your audioserver is installed. For me e.g. it was libsdl1.2debian-pulse.

I don't know about the renderer, maybe you could also check out libgl1-mesa-glx / -dri or something like that.

There is another client for linux as far as I know. It's q2max.

gl hf

---

### Post by jtarin on 2012-06-25
> **Rodney9 said:**
> 
Are there any other/better Quake 2 versions/mods for single play ?

RodneySure there are......[Here]("http://www.quaddicted.com/quake/recommended_engines")
One of the best [here]("http://icculus.org/twilight/darkplaces/").
Another [here]("http://www.kristianduske.com/fitzquake/").(which I use in Linux and Windows)

---

### Post by urata on 2012-10-28
But jtarin, those are actually all Quake ONE clients aren't they? I don't think they work for Quake 2.

This is how I got Yamagi Quake 2 to work.

Step 1. Download the yamagi-quake2 debian archive from [yamagi.org]("http://www.yamagi.org/quake2/debian.html")

Step 2. Open the archive with your Archive Manager.

Step 3. Drag the /usr/lib/games/yamagi-quake2 directory to your home folder (or wherever).

Step 4. Mount your Quake 2 CD and open it in your File Manager.

Step 5. Drag the /Install/Data/baseq2 directory into the yamagi-quake2 directory that you made in Step 2.

Step 6. Open a terminal inside the yamagi-quake2 directory.

```
chmod +x quake2
```

And to play the game you open a terminal in that directory and type.

```
./quake2
```

Although there are probably a hundred easier ways to run the game, but just double-clicking the icon doesn't work for me. Also running it in a terminal is useful because you get the feedback about errors.

I hope this helps someone get this working.

---

### Post by Signy on 2012-12-07
I have yamagi quake2 5.00 and it didn't use to run with error:
```
----- refresher initialization -----
Byte ordering: little endian

Input initialized.
Refresher build options:
 + Retexturing support
 + Gamma via X11
Refresh: Yamagi Quake II OpenGL Refresher
Shutting down Ogg Vorbis.
Shutting down OpenAL.
recursive shutdown
Error: Couldn't load pics/colormap.pcx
```After some time searching on the Internet I've found solution: in directory /usr/share/games/quake2/baseq2 I renamed:
```
PAK0.PAK -> pak0.pak
```and now it works fine...
Maybe someone else find it useful.

---

