---
title: "KDE and Pulseaudio"
date: 2011-08-25
forum: Desktop Environments
---

### Post by Atomic-Fanboy on 2011-08-25
Does anyone know why, when using the System Monitor, Pulseaudio has a nice value of -11 instead of zero (like everything else)?

It's not a problem, but is quite confusing.

---

### Post by tzily on 2011-08-25
you mean why does pulseaudio 'always' have the -11 niceness 
it's because that's it's default. audio always needs to have a high priority

---

### Post by Atomic-Fanboy on 2011-08-25
I don't want to sound argumentative, but although audio is a priority... so is plasma-desktop and kwin but they all have nice 0....?

---

### Post by tzily on 2011-08-25
don't you worry
linux nice doesn't work like in windows
in windows if you changed your winamp priority (for example) to the highest available selection, your system froze, right ? at least that's what was happening in my xp times
pulseaudio -11 nice is equal to your other 0 nice processes while idle, the only difference is made when your computer is 100% overloaded; and you will see that the sound plays fine! on 20mbit bluray 1080p video encode outputed in a crappy player like vlc with a bad renderer and no video acceleration, while the video is all choppy full of dropped frames
this is why nice is nice :)
so nothing affects you, but if you feel like customizing your entire system variables, go ahead. i prefer mine set as default ;)

---

### Post by Atomic-Fanboy on 2011-08-26
"in windows if you changed your winamp priority (for example) to the  highest available selection, your system froze, right ? at least that's  what was happening in my xp times" 

I got a laptop 2 years ago. (I'm using it to write this). My old system had XP, along with a single core processor and a pathetic 256 MB of RAM. If I touched ANYTHING, it froze. :P

---

### Post by Slim Odds on 2011-08-27
> **Atomic-Fanboy said:**
> "in windows if you changed your winamp priority (for example) to the  highest available selection, your system froze, right ? at least that's  what was happening in my xp times" 

I got a laptop 2 years ago. (I'm using it to write this). My old system had XP, along with a single core processor and a pathetic 256 MB of RAM. If I touched ANYTHING, it froze. :P

Never look directly at a windows machine..... :lolflag:

---

### Post by tzily on 2011-08-27
lmao

---

