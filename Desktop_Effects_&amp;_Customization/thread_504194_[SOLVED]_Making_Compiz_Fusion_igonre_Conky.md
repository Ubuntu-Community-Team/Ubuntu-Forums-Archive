---
title: "[SOLVED] Making Compiz Fusion igonre Conky"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by psyopper on 2007-07-18
Does anyone know how to make Compiz Fusion's Ring Switcher ignore my Conky? I absolutely love the ring switcher, but would like to see Conky left out of it. The plug-in shows how to *add* windows by type but there isn't an "exclude windows" feature that I can find.

I'm running a version from Trevino's repo's, but it's an older version from there, probably about a month old now. I stopped updating it when people were having performance and memory issues with it.

---

### Post by ThrobbingBrain66 on 2007-07-18
If Conky is being pulled in with the ring switcher, its "type" is one of the types listed in the box.  Do some intelligent guess and check by removing one entry at a time until you find the right one.  The first two I would try are 'utility' and 'unknown'

---

### Post by psyopper on 2007-07-18
I tried that with no luck. Actually at some point trying this bunked my flat-file completely and I subsequently spent about 20 minutes readjusting everything the way I liked. 

I also tried the Window Rules plugin and tried both "conky" and "(conky)" (without the quotes) in Skip Taskbar, Skip Pager, Below, Sticky, Widget, Non movable windows, Non resizable windows, Non minimizable windows, Non Maximizable windows and No Focus. This didn't work either.

I wonder... is there a way to tell Conky in the script what type of window it is?

Answer - YES. A quick peek at [the conky settings page on Sourceforge]("http://conky.sourceforge.net/config_settings.html") shows own_window_type with three options, normal, desktop, and override, normal is the default. I did not have this value in my conky.rc so the value was "normal" by default. Setting this value to desktop fixed my issue.

---

### Post by psyopper on 2007-07-18
Woops... not quite right. Turns out that this method causes some issues with Nautilus. Specifically - clicking on the desktop brings the desktop above Conky and Conky disappears.

hmmm...

I'm trying, at this very moment, the override setting in own_window_type. Still out of the Ring Switcher and staying above the desktop and below the other windows. I'll update if this changes.

---

### Post by psyopper on 2007-07-23
I actually found the right answer, with some interpretation and trial/error from [this thread on opencompositing.org's forum]("http://forums.opencompositing.org/viewtopic.php?f=51&t=529")

It comes down to adding the following to the end of your Ring Switcher - Ring Windows command
```

& !(class=conky | name=$conky)

```

Now I can run my conky with normal settings and it is ignored in the ring switcher!

---

