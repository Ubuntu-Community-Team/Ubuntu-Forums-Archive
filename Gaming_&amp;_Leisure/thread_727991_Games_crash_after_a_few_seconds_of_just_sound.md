---
title: "Games crash after a few seconds of just sound"
date: 2008-03-18
forum: Gaming &amp; Leisure
---

### Post by Aeonoris on 2008-03-18
Whenever I try to play a game (for example, gltron, supertux, epsxe, GW), a blank (black) window opens and waits for a few seconds, the sound starts working (or, at least, gltron's sound did), and then the window closes.  The output in the terminal is:

epsxe:
```
 * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [bios/scph1001.bin].
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
NVIDIA Corporation
                  GeForce FX 5600XT/AGP/SSE/3DNOW!
                                                   * Open gpu[0]
 * Init spu[0][libspuEternal.so.1.41]
 * Open spu[0]
Aborted (core dumped)

```

And for gltron:
```
[status] loading settings from /home/aeonoris/.gltronrc
[status] loading artpack 'default'
using min_filter: 9987 (setting: 3)
[scripting audio] found track ' song_revenge_of_cats.it '
[sound] initializing sound
[sound] loading song song_revenge_of_cats.it
wrap around in buffer (1880, 163560, 163840)
Aborted (core dumped)

```

Both GW and supertux freeze up my system, requiring a restart.  I am using the proprietary nVidia driver (the free one doesn't support 3d accel), and have a dual core processor (dunno if that helps).

---

### Post by acoustibop on 2008-03-18
AFAIK none of the Eternal sound plugins actually work in Linux, Aeonoris.  You'll have to use something like Pete's.

Better yet, try [pSX Emulator]("http://psxemulator.gazaxian.com/") instead of ePSXe: it works much better, especially in Linux.  Since it's pluginless, there's no complicated messing about sourcing plugins and configuring them.  You simply need to decompress the package, install libgtkglext1 (in the repositories), put a BIOS in the bios folder and you're good to go.  You can usually run it quite happily on default configuration, except for the controller, of course.

If you have Compiz or something like that running, try disabling it: it very often messes up 3D games.

---

### Post by Aeonoris on 2008-03-18
Err, it's not just a problem with epsxe, it seems to be anything that uses rendering, or something.  Normally I would say 3d rendering, but supertux is 2d...  Also, like I said, the sound is the only thing that actually -does- work, though if I have problems with it in the future I'll take your advice.
Edit: Oh, and what's Compiz?  Does it come already installed with kubuntu?  How would I turn it off, if I had it running?  There doesn't seem to be a process running under that name...

---

### Post by acoustibop on 2008-03-19
Compiz is the desktop manager that comes as part of Gutsy, Aeonoris and, I'm pretty sure, with Kubuntu as well.  If it works the same as Ubuntu, right click on your desktop, click Change Desktop Background, click the Visual Effects tab, select None and click Close.

---

### Post by Aeonoris on 2008-03-21
I couldn't find anything like that on Kubuntu, so I tried with GNOME.  GNOME wouldn't start (input not supported, doubtless a product of my struggling with the xorg.conf), so I reinstalled Ubuntu, and there's still the same problem.


Update, sometimes when I run gltron now it spams "buffer underrun!" a ton before closing.  Woot?

edit: Oh, and I have the visual effects set to "None".

---

### Post by BigRedButton on 2008-06-15
I have the same problem with Chromium B.S.W. (which is also 2D).

BTW is there any linux equivalent to DirectX that could be to blame?  I know of similar problems with games in Windows that were caused by DirectX.  

I do know there are rendering options in gltron and chromium (which we can't get to because we can't see them)... maybe they aren't set to OpenGl by default... just a thought.

edit:
I fired up gltron and killed it right away to see if I was missing anything at startup, and sure enough

[error] cannot load .gltronrc from /home/rocket/.gltronrc
[warning] old config file found, overriding using defaults
[warning] defunct config file found, overriding using defaults

so I looked for the file there and I didn't see it.  Is there a way to make one?  I'm sold on the idea that this is a problem with OpenGl.

---

