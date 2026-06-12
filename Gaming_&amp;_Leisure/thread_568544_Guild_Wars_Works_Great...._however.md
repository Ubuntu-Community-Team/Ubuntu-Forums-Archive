---
title: "Guild Wars Works Great.... however"
date: 2007-10-05
forum: Gaming &amp; Leisure
---

### Post by Drake2k on 2007-10-05
I've read up a few posts about GW but I wanted to start a new one as I didn't really think those had anything to do with this.  Ok so here goes.


Guild Wars.  It's gorgeous.  The install was flawless.  I'm only on the first 2 discs, no expansions yet.  There's only two annoyances.  They're annoyances because I can play the game just fine despite them.


Annoyance number one:
   I get these white squares in the scenery.  As I approach them they clear out.  They're not everywhere but they're often enough to be annoying.  They don't hide the entire scenery, maybe only a tree or a barn or something then as I approach it clears up.  They also appear in the beginning cinema and in towns.

Annoyance number two:
   The game locks up my entire computer when I try to exit.  I con log out and back out all the way to the log in screen however, when I try to exit that screen that's when the computer locks up.  There are still things running as I can hear my GAIM making noises.  I can't switch work spaces, alt-tab program, nor can I even reboot X with CNTRL-ALT-Backspace. 


Here's what I'm using.  
Wine version 0.9.46
ALSA Driver
  Hardware Acceleration - FULL
  Default Sample Rate - 44100  Bits - 16
  Unchecked Driver Emulation

Applications
  Windows - Windows XP

Graphics  
  "Allow the window manager to control the windows"
  Vertex Shader Support - Hardware
  "Allow Pixel Shader (If supported)

----
That's the configuration that works best with my World of Warcraft.
Any ideas or thoughts?

---

### Post by Drake2k on 2007-10-06
meow

---

### Post by cor2y on 2007-10-07
> 
Annoyance number one:
 I get these white squares in the scenery. As I approach them they clear out. They're not everywhere but they're often enough to be annoying. They don't hide the entire scenery, maybe only a tree or a barn or something then as I approach it clears up. They also appear in the beginning cinema and in towns.
Related to the version of wine, a guildwars update, whatever directx setting and video driver used when playing the game.
Sorry to say there are a lot of factors that can contribute to this, look in the [main guildwars thread]("http://ubuntuforums.org/showthread.php?t=283122") for some recommended fixes they will not always work if for example you update wine regularly or your video card drivers or the game gets an update (which you can't avoid).

> 
Annoyance number two:
 The game locks up my entire computer when I try to exit. I con log out and back out all the way to the log in screen however, when I try to exit that screen that's when the computer locks up. There are still things running as I can hear my GAIM making noises. I can't switch work spaces, alt-tab program, nor can I even reboot X with CTRL-ALT-Backspace. 
Never run games unless they are native Linux games in full screen.
Set wine to a windowed mode smaller than what your current desktop is you never know when a lockup of freeze might get you.

---

### Post by MonkeyBoy on 2007-10-07
The white box problem seems to be a common one.  I have grown to ignore it these days rather than mess about with my setup.

Your second problem I have no suggestion but I am able to run fullscreen and close the game normally so it is doable.

---

### Post by handy on 2007-10-07
I have never seen the white box problem, or had any problem closing GW.  The only minor problems I have is the need to turn off reflection's in the GW control panel due to slowing the frame rate too much in the few areas that contain reflections & the rmb needs a few clicks after zoning for mouse to function correctly.  I'm using Cedega 6 though, because I payed too much for it...

---

### Post by Drake2k on 2007-10-09
The windowed mode stopped the crashing Thanks Cor2y.  The White boxes has gotten progressively worse as I travel through the game.  It's down right annoying now and I can't see very far into the zone.  I have to rely on my mini map for guidance.  I'm not sure if it's the snow effects that are screwing things up or what but now even in the regular zones the boxes (white black or some strange pattern like a box crate) that appear instead of treas bushes or some other small landscape detail or getting pretty bad now.

ugh... I'm going to go through that thread as you suggested and see if I can dig up anything else.

---

