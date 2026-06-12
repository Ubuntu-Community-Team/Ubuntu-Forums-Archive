---
title: "[SOLVED] Compiz fusion Ok, but no emerald"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by ravimannan2002 on 2007-08-22
I installed compiz fusion last night using this guide:

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

 It works, but I can't get emerald to use a theme. Instead I can only get the themes from System>Preferences>Themes.  For a while, I couldn't get any window decorations, until I went into the compiz config-settings-manager and checked Window Decoration (D'OH!).  In the "command" textbox of that section I put "emerald --replace"  In my session, I have the commands "compiz --replace" and "emerald --replace".  I've tried many combinations of these commands I read from the forum, too, like:
compiz --replace -c emerald --replace&

I even have xorg.conf with 
Section "Device"
    Identifier     "<your display device name>"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
EndSection


Any ideas? Thanks!

---

### Post by njknight on 2007-08-22
If its any help my xorg.conf file has the following for my nvidia card

Section "Device"
    Identifier     "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection

and at the end

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by c.ovidiu on 2007-08-22
Yeah, same thing happens to me:

ovidiu@ovidiu-desktop:~$ compiz --replace -c emerald
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'
[...]

Looks like they removed the -c option for some reason. I have to do an "emerald --replace" in order to have the Emerald themes.

---

### Post by ravimannan2002 on 2007-08-22
That didn't work. This is the output when I do that in the command line:

```
me@laptop:~$ compiz --replace  emerald
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
/home/me/.themes/AquaMarine/gtk-2.0/icons/iconrc:78: Unable to locate image file in pixmap_path: "gtk-two-columns.png"
/home/me/.themes/AquaMarine/gtk-2.0/icons/iconrc:144: Unable to locate image file in pixmap_path: "rhythmbox-play.png"
/home/me/.themes/AquaMarine/gtk-2.0/icons/iconrc:148: Unable to locate image file in pixmap_path: "rhythmbox-pause.png"
/home/me/.themes/AquaMarine/gtk-2.0/icons/iconrc:225: Unable to locate image file in pixmap_path: "volume-medium.png"
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:123: Overlay image options specified without filename
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:133: Overlay image options specified without filename
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:144: Overlay image options specified without filename
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:532: Background image options specified without filename
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:532: Overlay image options specified without filename
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:950: Background image options specified without filename
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:1190: Unable to locate image file in pixmap_path: "notebook_top_flat.png"
/home/me/.themes/AquaMarine/gtk-2.0/gtkrc:1194: Background image options specified without filename

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6602): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'



```

---

### Post by c.ovidiu on 2007-08-22
No, it's just "emerald --replace". So you have to type two separate commands: "compiz --replace" and after that "emerald --replace".

---

### Post by ravimannan2002 on 2007-08-22
Ok, it works yippee! 

I decided to reinstall emerald. When I did, I got the same an  error that I had when I first installed emerald.  It complained about some file  from miro. Previously, synaptic said that emerald still installed ok, so I didn't think too much about the error.  Now I unistalled miro and then reinstalled emerald.  I know it doesnt make any sense, I can paste the error if someone can tell me the log file it's in.

I also tried seperate commands in my session.

Thanks for the help!



To recap, my Startup programs are:
compiz --replace
emerald --replace

In the CompizConfig settings manager, I have Window Decoration checked with this in Command:
emerald --replace &

---

### Post by ravimannan2002 on 2007-08-23
Now emerald isn't starting up consistently. After restarting, emerald didn't start. Any ideas? This is driving me insane....

---

### Post by Inxsible on 2007-08-24
to start up CF with emerald themes, hit Alt + F2 and type in```
compiz --replace -c emerald &
```If you do not have emerald installed, then install it first using ```
sudo aptitude install emerald
```

---

### Post by ravimannan2002 on 2007-08-24
Starting compiz fusion + emerald with Alt-f2 is not a problem. My problem is having emerald start up consistently when I login, on startup ....

---

### Post by Inxsible on 2007-08-24
> **ravimannan2002 said:**
> Starting compiz fusion + emerald with Alt-f2 is not a problem. My problem is having emerald start up consistently when I login, on startup ....
Then you can put in either ```
emerald --replace
``` or ```
compiz --replace -c emerald &
```in your sessions and then save it.

Go to System --> Preferences --> Sessions and add a new Startup Application. Go to Current Session tab and make sure you are running compiz fusion and emerald. Also make sure the order of compiz --replace is lower than emerald --replace. 

What's probably happening is that the order is the same and so emerald --replace is executed first and then compiz --replace which disables emerald, if you know what I mean.

Also, put the style for emerald --replace as restart, if you want it to start immediately again when its switched off or killed.

---

### Post by ravimannan2002 on 2007-08-25
I decided to install the fusion-icon I found on this forum. Now I just start that up in my Sessions>Startup Programs with 
fusion-icon --sleep 20

I think my problem is that compiz starts, emerald starts, then metacity starts, so I'm stuck with metacity instead of emerald. If I do that sleep command I think I'm ok.  

Is there anyway to prevent the gtk decorator from replacing emerald after it loads? I could rename /usr/bin/gtk-window-decorator, but I'd prefer changing some config file or something...

Thanks again!

---

### Post by ravimannan2002 on 2007-08-25
ok, this is what I did.

I edited the compiz starter,  posted here:
[http://ubuntuforums.org/showthread.php?p=3238612](http://ubuntuforums.org/showthread.php?p=3238612)
Except I added an "else-if".

```
# start emerald if present
if [ -x /usr/bin/emerald ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
	/usr/bin/emerald --replace &
# otherwise, start the gtk-window-decorator if present
[B]elif [ -x /usr/bin/gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
	/usr/bin/gtk-window-decorator --replace &
[/B]elif [ -x /usr/bin/kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
        /usr/bin/kde-window-decorator --replace &
	FALLBACKWM="/usr/bin/kwin"

```

I also changed the "fusion-icon --sleep 20" to "fusion-icon" at startup.
I restarted and everything is working ok now!!! This time I'm sure.....
\\:D/\\:D/

---

### Post by thecure on 2007-08-30
> **ravimannan2002 said:**
> ok, this is what I did.

I edited the compiz starter,  posted here:
[http://ubuntuforums.org/showthread.php?p=3238612](http://ubuntuforums.org/showthread.php?p=3238612)
Except I added an "else-if".


Thank you so much.

---

