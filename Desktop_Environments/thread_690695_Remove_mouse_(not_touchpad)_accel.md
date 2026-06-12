---
title: "Remove mouse (not touchpad) accel?"
date: 2008-02-07
forum: Desktop Environments
---

### Post by maximilion on 2008-02-07
Found a couple threads about accel, but they were about touchpads.

My mouse is a black logitech optical wheel mouse on ps/2 (detected correctly), which works fine in XP wihout accel and with medium sens.

How do I completely remove accel and vastly increase max. sens? Dragging the accel to minimum and sens to maximum moves the cursor about 20 pixels per inch :P

Thankful for any help with this since good mouse settings is vital for usability!

[Edit: If pointed to a how-to, I could make a .conf file or something for users who prefer 0 accel like I do :)]

---

### Post by tcommbee on 2008-02-08
i fiddled a bit with the settings and also according to some other thread ([http://forum.ubuntuusers.de/topic/13888/](http://forum.ubuntuusers.de/topic/13888/)) the solution is quite odd: you turn acceleration up and sensitivity down! (this is what the xset m 1 command in the referended thread does)

it works this way: gnome makes some calculations with the two slide bars, but generally the xserver has to settings, a multiplication factor for accelerated movement and a treshold speed (measured in pixels per undefined time unit) before accel kicks in. In contrast to windows, acceleration just multiplies normal movement by a constant factor, while the treshold is reached. if you turn down sensitivity to MINIMUM, gnome also scales down this treshold until it reaches 1px, meaning that any movement will be accelerated! you can now use the acceleration slider as sensitivity slider (with an Logitech MX512@1200dpi i only need about 40%) :D

you can also set these thing with gconf-editor, there they can be found in /desktop/peripherals/mouse. motion_treshold must be 1, motion_acceleration a value you like. it seems the latter is directly multiplied with your mouse-resolution, because i move about 1200px when i set this to 1

enjoy

---

### Post by maximilion on 2008-02-09
I don't feel comfortable with fiddling around, as you put it. I would like to know how it works.

I set acc to max and sens to min in Prefs/mouse, and I can clearly feel and see (in Gimp) the accel.


I wouldn't mind doing a bit of science on this. Since I do 3D design the mouse feeling is important to me, and I firmly believe that you cannot make the best OS in the world if you don't make the best mouse panel in the world 8) (since [M]ouse is such an integral part of WIMP)

I did the xset m 1 command, and that seems to give a more linear motion, but with strange skips in the motion!

There really is no good setting for my standard Logitech optical, so I wouldn't mind spending some time on this. My mouse is a clickety marvel in, hm, "the other OS" ;) on the same PC - but there I could remove accel yet up the sens to a perfect level.

Will look for applicable mouse utilities, if none exists I might code one. Any tips on a luxurious IDE for this type of app?

---

### Post by tcommbee on 2008-02-09
Really? i use this setting since your post yesterday and i quite like it! the only other option i know, but which i have not tested yet is inserting the following option in your xorg.conf input section:

Section "InputDevice"
...
Driver "mouse"
Option "Resolution" "200" 
...
EndSection

to set your mouse resolution to 200 dpi (which should vastly increase the speed). However the manual ([http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)) says, it doesn't work for all kinds of mice.

Edit: I wouldn't recommend setting accel to the max (using my "dark" way of doing things) as this gives a acceleration higher than 1 which means that 1 physical mouse pixel is multiple software pixels, which is definitely unacceptable for drawing. a setting off ~45% accel and any value for sensitivity maps the exact mouse movement to the screen. Love it!

Edit2: this is actually the "magic" of my hack - by setting "xset mouse 1 1", accel is not really accel but just keeps the physical speed, thus threshold doesn't matter even.

---

### Post by maximilion on 2008-02-12
Great that you've gotten a setting that you like. However, I can't see any way to increase or decrease sens after uset the xset command. As soon as I drag the sliders, it reverts to usual movement settings.

I would like to know more about exactly how it works, if there is a mouse panel with larger range and more option, and possibly how to read the physical mouse movement, so I can provide such an option if I make a game.

Some of us Love getting the perfect feel, especially for something as vital as the tool you use for all your work! :KS

---

### Post by tcommbee on 2008-02-12
this is caused by the formulas used in the dialog, which restrict possible values to a certain range. I'd only change the values in gconf, which has the advantage to allow float values in contrast to xset and doesn't restrict values in contrast to the dialog.

i don't know how games are doing it right now in linux, but doing xset 1 1 on startup and restoring the users settings on quit at least gives you the "raw" mouse data (as you cannot access the mouse devices directly as user space app).

---

### Post by maximilion on 2008-02-12
I'm not sure that's true for games running in Gnome windows, or for web games. Quake 3, for example has an option for either reading the raw mouse data or DGA. I wouldn't bet every single game reads mouse data raw.

But I do appreciate the gconf-editor tip, thanks! - I will try to find out even more... :)

---

