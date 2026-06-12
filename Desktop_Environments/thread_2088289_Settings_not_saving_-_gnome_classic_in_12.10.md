---
title: "Settings not saving - gnome classic in 12.10"
date: 2012-11-26
forum: Desktop Environments
---

### Post by Aquila99 on 2012-11-26
Help needed please!
I have just done a clean install of Ubuntu 12.10 (64 bit) and installed gnome running the "clasic" environment.

All runs well except some things do no not allow me to same the settings:

First noticed it with the "Weather Report" Applet.  Changing the preferences does nothing (I wanted degrees C, not F).

But more seriously, going into the workspace switcher, I tried to set it to 6 workspaces.  It just stays as 4 (even though the applet now shows 6!)  -  Panning with ctl-alt-arrows just shows 4 

Most of the other applets seem to work OK (so far).

I am not sure where to start diagnosing this issue ... any idea where gnome logs its errors?

Any help appreciated, I am stuck.

Cheers!

---

### Post by stinkeye on 2012-11-26
Are you using compiz in the gnome classic session?
If so, the *"Weather Report" Applet changing the preferences does nothing*... may just be a bug.
For the workspace switcher when using compiz in the classic session see [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12298058&postcount=5")

---

### Post by Aquila99 on 2012-11-26
Not sure if I am running compiz (excuse my ignorance).  How can I check this?
I just did an install of gnome from the package manager and selected gnome-classic at login.

I did a "ps -ef | grep compiz", and it showed nothing

I don't think that it is the bug that you refered to, as I can open windows in each of the different workspaces separately and move between them.  (Although I di notice that the switcher says 1 workspace)

---

### Post by stinkeye on 2012-11-26
At the greeter I have a choice of...
**Gnome Classic**.........Uses Compiz as the window manager
**Gnome Classic(no effects)**....Uses Metacity as the window manager

I use wmctrl to show current window manager.
```
sudo apt-get install wmctrl
```

Show window manager...
```
wmctrl -m
```

eg
> [COLOR="DarkGreen"]glen@Quantal:~$[/COLOR] **wmctrl -m**
Name: [COLOR="Red"]Compiz[/COLOR]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF


P.S. When logged into the **Gnome Classic(no effects)** session
I can change number of workspaces in the switcher and they are retained on reboot.
and
Using ccsm to change number of workspaces when in the **Gnome Classic** (uses compiz) session
is also retained when rebooting into Gnome Classic.

---

### Post by Aquila99 on 2012-11-26
Thanks for that.  I have learnt some new things...
Firstly, after I installed wmctrl, I got the same output as you.
Then I installed ccsm (it wasn't there), and found the settings for the number of desktops.  This worked great. (Still not sure why the settings on the workspace switcher don't work)

And still don't know why the weather applet won't change, but that as the least of my problems  :-)

---

### Post by stinkeye on 2012-11-26
Ye it's a bit confusing.
When using compiz as the window manager you really only have 1 desktop which
increases in size according to the number of
virtual workspaces you configured in ccsm.
This command shows the number of desktops you have...
```
wmctrl -d
```

Output when running compiz (my setup Res [COLOR="blue"]1680[/COLOR]x1050 with 4x1 workspaces set in ccsm)
```
[COLOR="DarkGreen"]glen@Quantal:~$[/COLOR] **wmctrl -d**
0  * DG: [COLOR="Red"]6720x1050[/COLOR]  VP: 0,0  WA: 49,24 1631x1026  N/A
```
Notice  I have 1 desktop with a resolution of **6720x1050** (6720=4x[COLOR="Blue"]1680[/COLOR])


Where as when running metacity when I configure the workspace switcher to use 4 workspaces, 
it sees 4  separate desktops each with a res of 1680x1050.
```
[COLOR="darkgreen"]glen@Quantal:~$[/COLOR] **wmctrl -d**
0  * DG: 1680x1050  VP: 0,0  WA: 0,24 1680x1026  Workspace 1
1  - DG: 1680x1050  VP: N/A  WA: 0,24 1680x1026  Workspace 2
2  - DG: 1680x1050  VP: N/A  WA: 0,24 1680x1026  Workspace 3
3  - DG: 1680x1050  VP: N/A  WA: 0,24 1680x1026  Workspace 4
```

---

