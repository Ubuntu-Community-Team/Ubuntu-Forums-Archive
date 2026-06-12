---
title: "feh with no window manager?"
date: 2010-12-08
forum: Desktop Environments
---

### Post by photoben on 2010-12-08
Hey there,

I'm taking apart an old (128mb ram, 800ish cpu) laptop to make a diy digital picture frame. Anyway, I was wondering if I could do a command-line install, and install xorg, as shown on [this page]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), and then use [feh]("http://packages.ubuntu.com/maverick/feh") fullscreen to display images.

Is this possible without a window manager? I'm relatively new to Ubuntu as a desktop system, so am not familiar with the graphical paradigms.

Thanks in advance for any help!

---

### Post by nothingspecial on 2010-12-08
It should be, however I`ve not tried.

You can run a slideshow in the frame buffer though without X using fbi.

It would be easier if all the photos were in the same directory, so
```

fbi -t n photo_directory/*
```Where* n* is the number of second you want each image displayed.

If you wanted to use recursive directories you would have to do something like this

```
fbi -t n $(find /parent_directory -type f)

```but I`ve never tried either -- theory only :D

---

### Post by photoben on 2010-12-08
Thanks. Didn't know about viewing images in the frame buffer, that's pretty cool!

I wonder, though, if I would be able to get transitions (just fade to the next image) using something else—know of anything off-hand?

Yes, they would be in the same directory. I plan on sharing it on our LAN using Samba, for easy access from Windows computers—not worried about security—and with a keystroke that would invoke a script to kill the image viewer and restart it, to get the new images. I assume that wouldn't be too hard.

---

### Post by bdaman80 on 2010-12-31
[FONT=Arial][SIZE=2]I am working on the same thing.  After reading this i can say Feh works with Xorg and no windows manager.  But my screen goes into powersaving mode and shuts off.  I tried this fix
[COLOR=Blue]
[/COLOR][/SIZE][/FONT]> [COLOR=Blue][COLOR=Black][COLOR=#000000][FONT=Arial]Setup xorg to not blank screen[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]     # Added custom xorg.conf file ( x -configure ) then saved to /etc/X11/xorg.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[COLOR=#000000][FONT=Arial]     # This add the following code to your xorg.conf file[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]    Section "ServerFlags"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Option "BlankTime" "0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Option "StandbyTime" "0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Option "SuspendTime" "0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        Option "OffTime" "0"[/FONT][/COLOR]
[/FONT][/COLOR][/COLOR][/COLOR][COLOR=#000000][FONT=Arial][COLOR=Black]    EndSection[/COLOR][/FONT][/COLOR][FONT=Arial][SIZE=2][COLOR=#000000][FONT=Arial]

and I went from a 5 minute off time to a 45 minute off time. But it still blanks out. Any Ideas?

Im on [/FONT][/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2]Ubuntu 10.04 Minimal install[/SIZE][/FONT]

[FONT=Arial][SIZE=2][COLOR=#000000][FONT=Arial] Thanks in advance
[/FONT][/COLOR][/SIZE][/FONT]

---

