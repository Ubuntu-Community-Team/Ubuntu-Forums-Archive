---
title: "UT2004 problems with graphics"
date: 2007-04-06
forum: Gaming &amp; Leisure
---

### Post by fidolip on 2007-04-06
I finally got my UT2004 to work under Ubuntu 6.06 and even was able to succesfully install the megapack.:-) Unfortunately, when playing a deathmatch (4th map in the single player, the first one with more than 2 players) I started having some troubles with graphics, i.e. once in a while it will all get.. weird? Dunno how to explain it - it looks like the textures unwrap from objects and covered my vision? Anyways, it's impossible to play, and even pressing 'esc' and bringing up the menu doesn't help.:o I don't know if that helps but that's the output off the console the first time I ran the game after installing the megapack:

```

fidolip@laptop:/media/sda4/unreal tournament 2004$ sh ut2004
Exporting DM-BP2-GoopGod.....Successful!
Exporting DM-BP2-Calandras.....Successful!
Exporting CTF-BP2-Pistola.....Successful!
Exporting CTF-BP2-Concentrate.....Successful!
Exporting AS-BP2-Thrust.....Successful!
Exporting AS-BP2-SubRosa.....Successful!
Exporting AS-BP2-Outback.....Successful!
Exporting AS-BP2-Jumpship.....Successful!
Exporting AS-BP2-Acatana.....Successful!
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

```

and I get the last two lines everytime I run the game. Does anyone know how to fix this problem? I have an Dell Inspiron 6000 laptop, 1.6GHz, 1Gb RAM, ATI Radeon X300 - I think that should be enough to play the game? At least on the lowest details?

---

### Post by Phenax on 2007-04-06
> 
Q: I get the following text on my console when I run the game:
Xlib: extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Is this a problem?
A: No. This means you aren't using an X server from Xi Graphics.
That message means we're looking for the X11 extension they use to
change screen resolutions, and having a non-XiG X server, you
don't have it. THIS IS NOT A UT2004 BUG. It's not a bug at all.
Xlib prints that "error", but we handle it gracefully.


Though you can probably run it with some modification. Just for preliminary to see if we can't make a quick fix, try running it be using this command in a terminal
```

LD_PRELOAD="/usr/lib/libGL.so" ut2004

```

---

### Post by fidolip on 2007-04-07
Here's what I got when I run this command:

```

fidolip@laptop:/media/sda4/unreal tournament 2004$ LD_PRELOAD="/usr/lib/libGL.so" sh ut2004
ERROR: ld.so: object '/usr/lib/libGL.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libGL.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libGL.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libGL.so' from LD_PRELOAD cannot be preloaded: ignored.
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

```

Btw. you might notice that I have to run ut2004 w/ command 'sh' <that's running a script command, ai?> and only when I'm in the directory when the game is installed. Is it possible to create a command 'ut2004' which can be ran from anywhere?

And even though 'ut handles this error gracefully' I still get this graphical crashes.:-( I think they dissappear when I change the graphic mode from OpenGL to software, but it's just not worth it - game looks awfully then.:/

---

