---
title: "HELP, tollbar gone"
date: 2009-01-06
forum: General Help
---

### Post by steck_638 on 2009-01-06
i started up my comp after moving it to my dads house, ive done it before with no problems and am always careful. but this time all my toolbars (i think thats what there called, they are in XP) were gone. i have had other minor problems where something was wrong so i just turned off my comp and turned it back on, it didnt work. so i tried again. still nothing. i though of recreating them but when i right click on the desktop the option isnt there. am i missing something or what?


also i think this is the right place for this but this is my first post here so im not 100% sure

---

### Post by fooman on 2009-01-06
if you mean the panels at the top and bottom of the screen...and they are completely gone (or are they there and just blank?),  then try this:

press alt-f2 and see if it brings up a "run program" box...if it does, then type this into it and press "run":

```
gnome-panel &
```

see if that works.

---

### Post by steck_638 on 2009-01-06
ya, they are completely gone

and nothing came up :(

---

### Post by fooman on 2009-01-06
ok,  try this...right click on the desktop and choose "create launcher"

in the box that pops up, type "terminal" for the name and in the command space type "gnome-terminal" (no quotes on those)...then press ok

that should put a launcher for a terminal on the desktop...click on it to bring up a terminal window.

in the terminal, type or copy/paste:

```
gnome-panel &
```press enter...see how that works.

---

### Post by blazemore on 2009-01-06
Try hitting Alt+F2 and typing
```
killall gnome-panel
```

---

### Post by steck_638 on 2009-01-06
nothing comes up when i right click and click create launcher and nothing comes up with alt+f2 (but the other hotkeys i know seem to work)

is there an icon somewhere i can use? i would be able to find it. i just tried killing the power as opposed to turning it of normally but still nothing


i found a terminal shortcut, when i put in gnome-panel &,
The program 'gnome-panel' is currently not installed.  You can install it...


killall gnome-panel,
no process killed (then it says something about an exit or something)


i think i will need to install gnome panel, but before i do something and mess something up can anyone verify that?

---

### Post by fooman on 2009-01-06
no, that should not mess anything up,  go ahead and install...in a terminal:

```
sudo apt-get install gnome-panel
```

---

### Post by ajgreeny on 2009-01-06
Try Ctrl+Alt+F1 to get to a console, login with your usual username and password (password does not show on screen) and then use ```
sudo apt-get install gnome-panel
```If that doesn't work try ```
sudo apt-get --reinstall ubuntu-desktop
``` which will ensure you have all the packages needed for ubuntu.  It may seem a bit over the top, but it will make sure everything is there.

---

### Post by steck_638 on 2009-01-06
ok, i have this now
ldconfig deferred processing now taking place

how do i get them back now, and what stuff is on the basic toolbars? do i right click on the desktop and choose "create launcher" or turn it off and it will be there when it comes back on?


i restarted and it all works fine now, all the toolbars i had are back

ty for the help, its done now :D

---

### Post by don_ on 2009-03-17
> **fooman said:**
> if you mean the panels at the top and bottom of the screen...and they are completely gone (or are they there and just blank?),  then try this:

press alt-f2 and see if it brings up a "run program" box...if it does, then type this into it and press "run":

```
gnome-panel &
```

see if that works.

I had the same trouble on my xubuntu laptop and this fix did the job!
Thanks
Don

---

### Post by lisati on 2009-03-17
> **don_ said:**
> I had the same trouble on my xubuntu laptop and this fix did the job!
Thanks
Don

When I had xubuntu on my other laptop, a *similar* trick worked, detailed somewhere in another thred.

---

### Post by don_ on 2009-03-17
> **fooman said:**
> no, that should not mess anything up,  go ahead and install...in a terminal:

```
sudo apt-get install gnome-panel
```

I ran this on my xubuntu laptop and now I have a toolbar like regular ubuntu instead of the toolbar that came with xubuntu
i like it

Don:popcorn:

---

