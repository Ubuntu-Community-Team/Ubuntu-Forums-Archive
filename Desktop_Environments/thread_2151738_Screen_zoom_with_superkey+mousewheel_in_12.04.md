---
title: "Screen zoom with superkey+mousewheel in 12.04"
date: 2013-06-05
forum: Desktop Environments
---

### Post by fatcatthetinker on 2013-06-05
I'm trying to get mousewheel screen zoom working again after a update from the previous LTS to 12.04 LTS with Gnome Classic. 

I use it to zoom in on pictures of text when detail is too small to see well on a 22" 1920x1280 screen. It's needed when viewing Googles old magazine articles with this monitor. It often allows zooming in on video for full screen when the full screen button causes stutter, so I used it a lot.

Super key+mousewheel worked before the upgrade.

Gear icon > system settings > keyboard > shortcuts > universal access gets me to where I might be able to enable  this, and I can change it to show mod2 +super l but it changes no function that I can see and scrolls rather than zooms when I try it.

Thanks, Harry

---

### Post by 3rdalbum on 2013-06-06
The zoom in feature is part of the Compiz window manager, which Gnome doesn't use by default. You will need to run this command:

compiz --replace

and then your zoom will either work, or be an option in Compizconfig Settings Manager.

---

### Post by fatcatthetinker on 2013-06-06
Thanks for the reply. I ran the terminal command and got this:

fatcat@fatcat-fast:~$ compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/fatcat/.compiz/session to /home/fatcat/.compiz-1/session
[LOG]: Copied file /home/fatcat/.compiz/session/10844c6530612ed1fd13656121532028900000024570040 to /home/fatcat/.compiz-1/session/10844c6530612ed1fd13656121532028900000024570040
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1c00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000014

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1000003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x321c3ad

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3400004

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x3600090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3600093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3600096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x360009a!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x360009a!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x360009d!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x360009a!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing cube options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "main_menu_key"
Setting Update "run_key"
Starting gtk-window-decorator
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct

........................
I never got a prompt though I waited 5 minutes after terminal action stopped and cpu activity dropped to idle.
I then closed terminal with process still running.

I see no noticeable change even after reboot.

Where do I find "Compizconfig Settings Manager" on my screen? is it where I refered to in my first post?

Any suggestions ?
Thanks, Harry

---

### Post by stinkeye on 2013-06-06
What session are you logging into?
```
echo $DESKTOP_SESSION
```

Is compiz the window manager.
```
sudo apt-get install wmctrl
```
```
wmctrl -m
```
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **echo $DESKTOP_SESSION**
ubuntu
[COLOR="#008000"]glen@Raring:~$[/COLOR] **wmctrl -m**
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
compizconfig-settings-manager needs to be installed.
```
sudo apt-get install compizconfig-settings-manager
```

Will show in dash or start in terminal with
```
ccsm
```

---

### Post by fatcatthetinker on 2013-06-06
All done as advised. How do I zoom? super mousescroll still scrolls, no zoom. Is there a new control for zoom?

Ah, so I have to do a search to find the Compiz controls. Most bizarre interface I have ever seen I think, and that's with decades of using computers. 

 I set up for super mouse button 1 zoom in and supermouse button 2 for zoom out. Which I assume are the left and right mouse buttons on my 2 button mouse. 

Still no zoom.

---

### Post by stinkeye on 2013-06-06
> **fatcatthetinker said:**
> All done as advised. How do I zoom? super mousescroll still scrolls, no zoom. Is there a new control for zoom?
In your first post you said you were using Gnome Classic.
The **Gnome-Classic(no effects)** session uses metacity as the window manager, so compiz zoom won't work.
The **Gnome-Classic** session uses compiz as the window manager and zoom will work.

---

### Post by fatcatthetinker on 2013-06-07
:KS 
Stinkeye, I have zoom working with super right click and super left click now, thank you very much.

I logged out of my session, clicked on the right icon in the log in icon to get it to show all my log in options. logged in in the gnome classic (not the no efects).

I then ran ccsm in the terminal and in the accessibility options clicked the enable box and clicked to the right of the enable box to open a hidden menu which allowed me to set up zoom in and zoom out as buttons 1 and 3. Had to increment the button # to 3 with the up arrow for the right click.

Works fine, I'm good till the next long term release.

Again, thanks to you and the rest of the folks that help out.

Harry

---

### Post by stinkeye on 2013-06-07
Yeah, I thought you were in that session.
Something you may not know, when in the gnome-classic session with compiz,
to edit the panel you need to alt+Super+rightmouse.
Goodluck.

---

