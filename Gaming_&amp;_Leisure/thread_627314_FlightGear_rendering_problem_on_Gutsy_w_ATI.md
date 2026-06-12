---
title: "FlightGear rendering problem on Gutsy w/ ATI"
date: 2007-11-29
forum: Gaming &amp; Leisure
---

### Post by nandim. on 2007-11-29
When the game loads I get strange colors (solid black, white, yellow and orange at most) on everything (planes, terrain, sky, panel)... 
I used apt-get to install it.

I'm using a fresh install of Gutsy, have installed ATI newest driver with ENVY.
All other games and programs works fine (i.e True Combat), GoogleEarth and Compiz.

OBS: compiz was off when I start it.

Anyone has the solution? or the same problem?!

thx

---

### Post by librano on 2007-12-30
hi,

i am facing the same problem... its like the textures are not being rendered... i can see the outline of the cockpit dash, the terrain and sky.. but no textures... anybody got any fixes?

I am using the ATI drivers installed using Envy on a GUtsy-based system.

---

### Post by viciouslime on 2007-12-30
Are you usin 1.0.0 or the one in the repos? I had a problem with strange white "triangles" appearing across the sky. My solution was to change the menus so they're not transparent. To do this, open ~/.fgfs/autosave.xml and edit:
```
<gui>
      <current-style type="int">1</current-style>
      <devel-widgets type="bool">false</devel-widgets>
    </gui>
```

To read:
```
<gui>
      <current-style type="int">1</current-style>
      <devel-widgets type="bool">false</devel-widgets>
    </gui>
```
Notice the 0 has become a 1. Not sure if this will help you guys though...

---

### Post by visionary on 2008-01-13
Maybe you could try the following which i harvested from some other websites which helped me greatly with Flightgear in Gusty....

1)When you start flight gear, consider starting with the following options in your command.... (You can read more from here [http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html](http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html) )

> --control=mouse
> --disable-intro-music
> --disable-random-objects
> --disable-sound
> --disable-hud-3d
> --disable-specular-highlight
> --fog-fastest
> --model-hz=60
> --geometry=800x600
> --visibility=10000.0
> --fov=50
> 
> --prop:/sim/rendering/static-lod/detailed=500
> --prop:/sim/rendering/static-lod/rough=5000
> --prop:/sim/rendering/static-lod/bare=15000
> --prop:/environment/clouds/layer[1]/coverage="clear"
> --log-level=alert

That actually improved a little.....Now for the biggest improvement i go was to to do the following.....

2) downloaded driconf (sudo apt-get install driconf)

3)Then edit device section of /etc/X11/xorg.conf to show as

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
[B]BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "AGPFastWrite" "true"
Option "EnableDepthMoves" "true"
Option "GARTSize" "64"
Option "AGPSize" "64"
Option "backingstore" "on"
Option "UseInternalAGPGART" "no"[/B]
EndSection


Though i am using Nvidia card, i added those lines (in bold)  in my xorg.conf file.

Now restart your system and enjoy your flight gear.
Hope that helps!

Cheers!

---

### Post by FokkerCharlie on 2008-02-25
Hi

I don't know if you/anyone else is still having the same problem, but I found a solution to mine:

Start FG in the normal way. Select 'View' drop-down menu (one from the left- you may not be able to read the labels!) Select 'Rendering Options' (fourth choice) Uncheck 'Use Point Sprites for Runway Lights' (fourth check-box)

When you come to quit FG, do so by menu: File...Exit, rather than closing the window to save this setting.

I hope that this works for you, and you can enjoy FlightGear.

Charlie

---

### Post by rosendahl on 2008-03-01
> **FokkerCharlie said:**
> Hi

I don't know if you/anyone else is still having the same problem, but I found a solution to mine:

Start FG in the normal way. Select 'View' drop-down menu (one from the left- you may not be able to read the labels!) Select 'Rendering Options' (fourth choice) Uncheck 'Use Point Sprites for Runway Lights' (fourth check-box)

When you come to quit FG, do so by menu: File...Exit, rather than closing the window to save this setting.

I hope that this works for you, and you can enjoy FlightGear.

Charlie

Thanks, worked for me.

---

### Post by cykze on 2008-03-10
This is what it looks like for me:

[Picture 1](http://hem.bredband.net/b362807/fgfs_init.png)
[Picture 2](http://hem.bredband.net/b362807/fgfs_in_game.png)

Does it look the same for you?

---

### Post by rosendahl on 2008-03-10
> **cykze said:**
> This is what it looks like for me:

[Picture 1](http://hem.bredband.net/b362807/fgfs_init.png)
[Picture 2](http://hem.bredband.net/b362807/fgfs_in_game.png)

Does it look the same for you?

It looked exactly like that. It helped turning 'Use Point Sprites for Runway Lights' off.

---

### Post by cykze on 2008-03-10
Isn't this the second menu and then the forth choice?
[http://hem.bredband.net/b362807/fgfs_view_menu.png](http://hem.bredband.net/b362807/fgfs_view_menu.png)

That just shows this window:
[http://hem.bredband.net/b362807/fgfs_window.png](http://hem.bredband.net/b362807/fgfs_window.png)

Thus no "fourth check-box".

Am I missing something?

---

### Post by rosendahl on 2008-03-10
Check my screenshot, I think it helps. :)

---

### Post by cykze on 2008-03-10
Strange. You have 10 choices in the View-menu whereas I'm just having 6. Perhaps we don't have the same versions. I'm using the flighgear package (0.9.10-2ubuntu) from the Gutsy universe repository. Do you use the same?

---

### Post by rosendahl on 2008-03-10
No. Installed from debs found here:
[http://www.getdeb.net/app/FlightGear](http://www.getdeb.net/app/FlightGear) (1.0.0)

---

### Post by cykze on 2008-03-10
Now it works! Thanks a alot!

---

### Post by FokkerCharlie on 2008-03-22
cykze

If you can't see that menu option, try starting FG from FGrun graphical launcher.  For some reason, starting from the command-line resulted in a similar situation for me, too.

Charlie

---

### Post by Doctor Drive on 2010-02-21
Installed flightgear from ubuntu karmic repos.
The minimun system requirements says
* Processor: 800 mhz / memory RAM: 256 MB / 32mb 3D Graphic Card

i've got 634 Mhz processor, 384 RAM, 32mb 3D Graphic Card...
Graphic drivers are properly installed...
-----------
When I load flightgear my 384 RAM loads fully and 512 MB Swap loads 79%...
looks loke a slideshow, the system almost hagngs up, like i'm trying to run it's a NFS Shift on dendy...

What's The Problem??

---

