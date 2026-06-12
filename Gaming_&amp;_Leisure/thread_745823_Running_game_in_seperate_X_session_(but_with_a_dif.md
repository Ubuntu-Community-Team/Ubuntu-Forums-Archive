---
title: "Running game in seperate X session (but with a different xorg.conf?)"
date: 2008-04-04
forum: Gaming &amp; Leisure
---

### Post by HunterK on 2008-04-04
I run my desktop @ 1280x1024 75Hz.  (This is the only refresh rate that allows compiz to run butter smooth when I drag windows.)  However, when I run my games, I would like to run the m @60Hz.  There is some wacky tearing effect in the game, but only when using 75Hz.  This effect is not present when running @60Hz.

I use a script to start a separate session just for the game, and I guess my main question is:

Can that new X session be started with a DIFFERENT xorg.conf file that the one I normally use?  One that is exactly the same except that it defaults things to 60Hz?

Here is the script:

```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
sudo X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "/home/ken/.wine/drive_c/Program Files/Steam"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game
xset m 0 0
DISPLAY=:3 WINEDEBUG=-all wine Steam.exe -applaunch 380 -novid -dxlevel 80 -refresh 60 -fullscreen -heapsize 512000
```

Is there something I can add to the **X :3 -ac** command to tell it to use a different xorg.conf file?

Thanks.

---

### Post by FrozenFox on 2008-04-05
Xgame can use a different xorg.conf. I don't know how to do what you are asking, but you may want to look at its source code (or use it for what you want, it does the same thing).

---

### Post by HunterK on 2008-04-05
I've decided to ditch the whole separate x session thing.  I'm using xrandr in a script just before I launch the game.  Then I have xrandr switch it back after the game is done.  Seems to work very well.

Example:

```
#!/bin/sh
xrandr -r 60
zsnes
xrandr -r 75

```

---

### Post by vdobriakov on 2008-11-26
According to `Xorg -help` you can choose the configuration file with `-config {relative_file_name}`. You can also use an absolute path, but need to run X as root for that. And it really works on my Ubuntu 8.04.

---

### Post by Novae on 2009-07-20
> **HunterK said:**
> I've decided to ditch the whole separate x session thing.  I'm using xrandr in a script just before I launch the game.  Then I have xrandr switch it back after the game is done.  Seems to work very well.

Example:

```
#!/bin/sh
xrandr -r 60
zsnes
xrandr -r 75

```

I do this however i find that it moves all of my other open windows onto one of my monitors when i re-enable it. Like, when i do the first xrandr it moves all the windows onto the primary monitor and then when i do the second they all map onto it. Any idea's?

---

