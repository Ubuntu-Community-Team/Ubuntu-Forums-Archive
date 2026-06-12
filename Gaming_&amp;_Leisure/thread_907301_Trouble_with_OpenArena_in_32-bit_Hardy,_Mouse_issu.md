---
title: "Trouble with OpenArena in 32-bit Hardy, Mouse issue"
date: 2008-09-01
forum: Gaming &amp; Leisure
---

### Post by Lance423 on 2008-09-01
Hi, I finally installed Ubuntu Hardy on my laptop, have everything up and running except for this one issue with OpenArena involving the cursor and mouse. I can load the game navigate thru the menus and play perfectly for about 8 minutes, but after that my cursor starts being able to move outside of the window I'm running in and I can't seem to get it to stay inside and turn my character the way I need it to. I've tried setting Space to mouse look and holding it, going fullscreen, and neither of these has worked. My screensaver is set to run after about 9 minutes, I don't think that would be interfering to.
If it helps I'm running 32-bit Ubuntu 8.04 LTS "Hardy Heron" on an HP Pavilion dv6704nr, I have all of my drivers set in place properly, and this is the only application I'm having issues with. I googled it to no avail, googled it again with "site:ubuntu.com" still nothing so I'm sorry to trouble people with such a simple problem but I loved Quake 3 and Openarena is something I would LOVE to get a good experiance out of. Any help would be greatly appriciated.

---

### Post by tjwoosta on 2008-09-01
hmm strange...

have you tried disabling compiz and playing?

to disable compiz run this command from the run dialogue (alt-f2) **NOT FROM THE TERMINAL**
```
metacity --replace
```

after playing your game you can turn compiz back on like this 

to re-enable compiz run this command from the run dialogue (alt-f2)
**NOT FROM THE TERMINAL**
```
compiz --replace
```


if that doesn't work then the only other thing i can think of is that the screensaver might be kicking on in the background and messing up the game, but i think you said thats not the case

---

### Post by Lance423 on 2008-09-01
Alright, thank you I'll try this ASAP, but it'll have to wait as I have meetings, I'll edit when I find out if this works or not.

EDIT: Alright, thank you very much that does the trick. Now I can enjoy OpenArena without worrying about when my cursor is going to decide to run away. :D

---

