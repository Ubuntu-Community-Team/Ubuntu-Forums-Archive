---
title: "Compiz Help Please"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by Grellin on 2007-10-30
Hey all. I know this is going to be a stupid question but I have to ask. Been looking at the forum threads for a few hours now and more than likely I am using the wrong search strings. 

Here is my problem. I have installed the compiz manager and from what I can tell it is working as advertised. I turn on opacity and it works. Wobbly windows, water, fire and a bunch more all work. What I can figure out or find directions on is how to enable the cube desktop display. I have it checked along with rotate cube, which unchecked desktop wall, but my desktop looks the same as always. Any ideas what I am screwing up here?

---

### Post by It_Was_Luck on 2007-10-30
Besure you have the columes set to 4 and the rows set to 1. This will give you the four desktops you need to enable the cube effect. Then either hold down the middle button on the mouse and move to see the cube, or press and hold Ctrl + Alt + Left Side of Mouse, this way will also allows you to go into cube-mode.

hth

---

### Post by Grellin on 2007-10-30
I'm sorry. I am fairly new to Ubuntu. When you say columns and rows, where is that setting? I have 4 desktops set. Also, middle mouse button doesn't do anything but ctrl+alt+LMB lets me twist the desktop around as a single dimension plane.

---

### Post by Zorael on 2007-10-30
General Options -> Desktop Size

Horizontal virtual size -> 4
Vertical virtual size -> 1
Number of desktops -> 1

---

### Post by Grellin on 2007-10-30
Thanks. That got it working! 

Just out of curiosity, what are some of the settings in Compiz you would recomend? I am really enjoying this but have yet to really tap into what I see as a major improvement in desktop management.

---

### Post by Zorael on 2007-10-30
I fiddled around something fierce, and the profile I ended up using has the following plugins enabled:
[LIST]
[*]Desktop Cube
[*]Expo
[*]Rotate Cube
[*]Viewport Switcher
[*]Fading Windows
[*]Minimize Effect
[*]Window Decoration
[*]Wobbly Windows
[*]JPEG, PNG, Svg, Text
[*]Crash Handler
[*]Cube Caps
[*]Regex Matching
[*]Resize Info
[*]Video Playback
[*]Workarounds
[*]Application Switcher
[*]Group and Tab Windows
[*]Move Window
[*]Resize Window
[/LIST]

Expo is awesome, I use it lots more than I use the cube. Fading Windows is nice but buggy with KDE Log out screen. Wobbly Windows since it's made of win. Group and Tab Windows since it's a brilliant idea, and if you can just remember to use it, could make your desktop(s) less cluttered.

I don't use Animations - they're a bit over the top, and I feel pretty content with just Fading Windows and Minimize Effect.

On almost every graphical effect I have slowed the movements down to make it extra smooth. It's probably more CPU intensive, but I don't mind much.

For instance, Minimize Windows. Speed 0.7, Timestep 0.5, Shade Resistance 80.
Rotate Cube. Flip Time 250, Speed 1.1, Timestep 0.7, Zoom 0.2.


You *will* want to tweak stuff in General Options -> Display Settings to get the best performance. Detect Refresh Rate makes things run less smooth, since it somehow detects a lower refresh rate than what you actually have, or something like that. On the other hand, I hear disabling it could make hibernating/suspending impossible - I haven't tried it yet.

To see if you can still squeeze out better framerates, disable VBlank there and lift Refresh Rate up to 100. If stuff is smooth but it tears a lot, you know there's still some muscle left unused. Tweak tweak.

---

