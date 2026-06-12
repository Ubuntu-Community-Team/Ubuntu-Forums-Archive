---
title: "TV-out and movies"
date: 2004-12-29
forum: Desktop Environments
---

### Post by Obi-Lan on 2004-12-29
Hi

I like to watch movies (DVD and Xvids..) from my computer through my TV. I got Radeon 9800 and  fgrlx installed (OpenGL version string: 1.3.4641 (X4.3.0-3.14.6)) and TV-out is working quite fine. For now Im using clone mode and when I run movies with MPlayer and X11 video driver I see the video on the TV too. The Problem is that when I try to watch these movies in fullscreen mode the playback turns very sluggish. When I use XV video driver theres no performance problems but no video on TV.

In Windows there is a feature called theater mode which is IMO quite perfect. Is there anything similiar solution in Linux? Or any other ways to watch movies from TV with fullscreen? ;)

---

### Post by dave_euser on 2004-12-29
most video cards allow the XV window to only be attached to one display output at a time - you'll need to find someway to switch this over to the secondary output (your TV). A quick search through google didn't pull up anything of serious note (though this has some info: [http://fedoranews.org/contributors/youssef_makki/tvout/](http://fedoranews.org/contributors/youssef_makki/tvout/))

What I'd try is using the MonitorLayout option in your X config to set your TV as the first device, and the LCD/CRT as the second. Might force the xv port to attach to the TV. Not ideal, but might work.....

Another option is to use OpenGL to display video instead of XV. I've never tried it before, but should be enough to scale video up to full size without bogging down your CPU.

---

### Post by ulrich on 2004-12-30
hi,
similar setup here...

i cant remember if i choosed clonemode while configuring, but with this setup i have one desktop on each monitor-device.
for watching a movie on the tv, i move my mouse over to the tv-desktop and open the player (mplayer or totem) and play the video from there.

this works painlessly.

these are the relevant parts of my xf86config
```

    Option "DesktopSetup"               "0x00000100" 
    Option "MonitorLayout"              "CRT, STV"

Section "ServerLayout"

    Screen "Screen0"
    Screen "Screen1" RightOf "Screen0"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

```

hope this helps

---

### Post by Obi-Lan on 2004-12-30
Ookay..

No idea how to make OpenGL work..

But I changed settings so that now I have dual head configuration. The problem is that any window manager doesn't load on the TV screen (screen1). I got xfce4 in screen0 which is my monitor. How do I load window manager I want to screen1?

---

### Post by dave_euser on 2004-12-30
[QUOTE=Obi-Lan]Ookay..

No idea how to make OpenGL work..

But I changed settings so that now I have dual head configuration. The problem is that any window manager doesn't load on the TV screen (screen1). I got xfce4 in screen0 which is my monitor. How do I load window manager I want to screen1?[/QUOTE]

You might have to set the Xinerama option in your X config file....otherwise, it treats each screen as independant, and not as one virtual screen.

OpenGL and Xinerama has had problems in the past - not sure what the current status is....

---

### Post by Obi-Lan on 2004-12-31
Well I think that the optimal solution woul be to load some very light window manager (or not at all) and very big button which starts gmplayer to the tv screen :)

Well it costs nothing to try xinerama anyway...

---

