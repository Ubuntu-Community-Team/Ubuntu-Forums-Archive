---
title: "Liquidwar/Allegro Problem"
date: 2005-05-02
forum: Gaming &amp; Leisure
---

### Post by Horn on 2005-05-02
I'm trying to get liquidwar running but whenever I execute it the screen goes blank and my monitor turns off.  I've piped the output and included it below.  I'm using the fglrx video driver for my Radeon 9700 pro and other games work so I'm not quite sure what the problem is.

The last line is when I managed to kill the xserver in another terminal.

```
liquidwar: built with a non-Debian (or old) Allegro, running glue code
liquidwar: everything went fine
Starting Allegro (http://www.talula.demon.co.uk/allegro)

Allegro ID : Allegro 4.0.3, Unix

Loading config options from "/home/carlin/.liquidwarrc" - failed...
Installing timer (driver="Unix pthreads timers") - success!
Installing keyboard (driver="X-Windows keyboard") - success!
Installing mouse (driver="X-Windows mouse") - success!
Installing sound (digi="Open Sound System", midi="DIGMID") - success!
Installing joystick (driver="No joystick") - success!
Setting up network - success!
Allocating 16 Mb - success!

Loading data from "/usr/share/games/liquidwar/liquidwar.dat" - success!
Loading fonts - success!
Loading maps - success!
Loading background bitmap - success!
Loading sound fx - success!
Loading textures - success!
Loading map textures - success!
Loading water sounds - success!
Loading midi music - success!

Loading custom textures from "/usr/share/games/liquidwar/texture" +++++ - success!
Loading custom maps from "/usr/share/games/liquidwar/map" ++++ - success!
Loading custom musics from "/usr/share/games/liquidwar/music" + - success!

Changing video mode to 640x480, fullscreen (driver="X11 fullscreen") - success!
X connection to :0.0 broken (explicit kill or server shutdown).
```

---

### Post by darkazurka on 2009-01-02
Once upon a time sound worked for me in liquidwar 5, but now I see there's no sound but just an insistent high frequency beeeeeeeeeeeep.

Is it because it's using the open sound system (OSS), instead of ALSA?

---

