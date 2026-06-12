---
title: "Dual screen setup - main screen?"
date: 2009-03-18
forum: General Help
---

### Post by RhysTheNewGuy on 2009-03-18
Hi there, I recently got Ubuntu 8.10 running with 2 monitors (of different size) using Twin-View and NVidia-settings, is there a way to set my larger monitor to be the "main" one, with the login screen, and my AWN bar on there?

it Currently looks a bit like this:


Smaller screen        :         Larger screen
    AWN               :
     
if that makes any sense.

Thanks :)
Rhys

---

### Post by Archimedes0212 on 2009-03-18
What do you have for a graphics card?

I know on my laptop I have an ATI graphics card and a program, called ATI Catalyst Control Center, was installed with my graphics driver in ubuntu.  Through this program I am able to customize my dual monitors however I like.  You may want to look into it if you have ati (I believe it's aticcc on the command line, but I may be mistaken [I'm away from my ubuntu machine currently] ) or into something similar that corresponds to your graphics card.

---

### Post by nacho_dh on 2009-04-30
I know the thread is old, but this might be useful for someone with the same problem...

I have Ubuntu 8.10 on a Dell E6400 with an Intel graphics card, and all i'm using to configure my dual screen is gnome's screen resolution tool.

Apparently there's no way to change which is the main screen since gnome's dual screen config uses xrandr that assigns the VGA output as the default screen for intel cards (more info: [http://ubuntuforums.org/showthread.php?t=1110407](http://ubuntuforums.org/showthread.php?t=1110407)), all u can do is moving the panels to the other screen, that's as close as u can get to change the main screen; pop ups and new windows will come up on the 'real' main window (vga) though.

---

### Post by i.r.id10t on 2009-04-30
It will depend on which port on the video card the monitor is plugged into.  Just swap 'em and move 'em on your desk if needed.

---

### Post by ladydeth666 on 2009-04-30
Ive got a BFG 8500gts, running a 22in on the left side, and a 19 on the right.  I let nvidia do all the controlling :)
My only problem was getting Wine to run games (Warcraft) in just the left side.  I ended up using Devil's Pie that I found in one of the gentoo forums [here...]("http://forums.gentoo.org/viewtopic-t-420196.html")

linked from this ubuntu forum...
[http://ubuntuforums.org/showthread.php?p=7128192](http://ubuntuforums.org/showthread.php?p=7128192)

---

