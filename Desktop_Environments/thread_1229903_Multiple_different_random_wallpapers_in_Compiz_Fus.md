---
title: "Multiple different random wallpapers in Compiz Fusion?"
date: 2009-08-02
forum: Desktop Environments
---

### Post by Lasombra Demon on 2009-08-02
Hey there!

I've been looking for something like a Wallpaper Spinner (something that randomly changes your wallpapers from a given list within a given amount of time, maybe with a nice fading effect), and, well found tons of stuff that works nice... when I'm letting Nautilius draw my desktop. 
If I do that, I have to keep the same wallpaper on each side of my five-sided prism desktop set (at least, when rotating the prism), which is something I don't want (I want a different image on each side, so I'm not letting Nautilius draw and have instead Compiz Fusion's wallpaper plugin enabled).

What I'm looking for is something that randomly changes the wallpapers in the CompizConfig Wallpaper settings from given lists, for each different desktop.

Is there something like this? :confused:

Thanks in advance!

---

### Post by peakpc on 2009-09-19
webilder works well on gnome. [http://www.webilder.org/]("http://www.webilder.org/")

It will not help with having a different wallpaper on each desktop but, it does allow automated switching based on time. nice GUI. not Compiz dependent.

---

### Post by Lasombra Demon on 2009-09-21
Hey there! Thanks for your reply!

I'm pretty much a newbie to the scene, recently moved from Windows to Ubuntu, and I'm struggling to get my desktop look exactly like I want it to. Finding so many options and so much tweakable stuff is both an incredibly rewarding and a challenging and terrifying experience! ^_^'

This post will mostly describe *what I would like to achieve*, what I've tried, and what I've succedeed in, regarding the whole GUI experience.

So, I go and read the tutorials, install ccsm, manage to disable Nautilius' show desktop (and put Cairo Dock so I can quick-access my stuff) to let the Wallpaper plugin draw my nifty hexagon-based prism desktop with a different pic in each workspace, specially when spinning the cube (something independent wallpaper programs don't do) and identifying the face you want to go to.

Disabling Nautilius' show desktop is no prob, though... but* the Wallpaper plugin doesn't have a 'rotate' option or anything, and I would like my Wallpapers to change automatically (from day to day, maybe one for each day of the week, maybe on a cube-spin basis, etc... and this done @ random or not), and have a specific group of wallpapers assigned to each workspace*.
Now, I could actually write a script to do this (once I master Bash a bit more) that edits the .profile file, but I also thought this would be a nifty feature, with a fade effect, etc.

That's until I found xwinwrap. Animated desktops! :O 

So, I thought about having xwinwrap handling my 'wallpaper rotate' idea. I got into xscreensaver to configure glslideshow to get ONE of my directories with pics, and... there are no chances of having different slideshows via glslideshow or any other screensaver at the same time (I thought there might an argument to specify the directory from where to read the images). No biggie here, since pretty much every command-line-supporting image viewer has a 'slideshow' option. I decided to use feh, because of the incredible amount of options it has. 

[I]So, I try to fire up xwinwrap with feh.

If xwinwrap works like charm like this...
xwinwrap -ni -o 0.9 -fs -st -sp -a -nf -- mplayer -wid WID /home/USUARIO/Pictures/WallpaperSet1/1.AVI -loop 0

and this

xwinwrap -ov -fs -- /usr/lib/xscreensaver/glmatrix -root -window-id WID

I wonder, what am I doing wrong here?
xwinwrap -ni -fs -s -st -sp -b -nf -- feh -window-id WID /home/USUARIO/Pictures/WallpaperSet1

xwinwrap -ni -fs -s -st -sp -b -nf -- feh /home/USUARIO/Pictures/WallpaperSet1[/I]

xwinwrap -fs -b -- feh /home/USUARIO/Pictures/WallpaperSet1[/i]

I wanted to try another solution, and bumped into this:
[http://forum.compiz-fusion.org/showthread.php?t=10507](http://forum.compiz-fusion.org/showthread.php?t=10507)

That + feh's incredible tweakability.

feh -q -p -z -F --stretch -D 1 -Z -x --next-button 99 --zoom-button 99 --menu-button 99 --rotate-button 99 /home/USUARIO/Pictures/WallpaperSet1

Now, since I have access via command line to what I input to my desktop, I just can do pretty much anything. I even used Opacify to make it semitransparent and show another wallpaper behind it.

But that's not all of it. Well, after all this, I know I will be able to do some stuff (running feh + the stuff from your tutorial), but there is still one little thing. *Whenever I'm rotating my prism-like desktop, if there are non-minimized windows, they won't be drawn unless I re-enter that workspace. The only windows actually drawn with effects and such (like reflections) are those from the last active workspace... and so, my nice feh and xwinwrap backgrounds (and some other stuff, like Audacious' playlist window, or even Screenlets, though I did configure them properly) aren't drawn when spinning the cube if I have ANY windows non-minimized on the whole desktop (6 workspaces), which is quite usual.* [IMG]http://forum.compiz-fusion.org/images/smilies/pidgin-smilies/sad.png[/IMG]

Any help you can give me on this? That's pretty much the only thing I haven't been able to solve...

Thx for yer time!

Another thing: I noticed I've disabled 3D windows, and this last little glitch is gone. I tried two possible fixes: 
One, just adding a !feh to 3D win's detection. This causes a bug in which the taskbar is distanced upon spinning the cube, like a window. I guess it's a conflict with the Window Rules I've set. :P
The other one, running devilspie and having it change the window type of feh, so it ain't normal, so it isn't 'detected' by the | Normal | Toolbar | etc part of 3D Windows. It didn't work either.

I guess I'll have to be without 3D windows. A shame, but I suppose I'll live.

---

