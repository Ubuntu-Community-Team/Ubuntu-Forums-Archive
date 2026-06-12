---
title: "accidentally disabled unity through compiz manager!!!"
date: 2015-04-04
forum: Desktop Environments
---

### Post by an3urysm on 2015-04-04
Hi guys. I just installed ubuntu 14.04 . 

I installed compiz fusion and emerald theme manager following instructions on a blog. 

It was mentioned to tick the windows decorator box under effects. Then a pop up came up, something about 'unity' and I accidently disabled it.


Now there is no box around my windows. When i restarted, it just shows the wallpaper...!  :((

How do I fix this?

Edit:
I tried to access terminal with alt ctrl f2.
Tried 'unity --reset', but it says
Warning: no display variable set, setting to :0
Error: the reset option is now deprecated

---

### Post by CantankRus on 2015-04-04
Go to a tty with ctrl+alt+F1
Login and run these 2 commands to put a terminal shortcut on your desktop.
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop 
chmod +x ~/Desktop/gnome-terminal.desktop
```
Type "exit" and hit enter.
Hit ctrl+alt+F7 and login to your normal session at the greeter if not already logged in.

Then use the terminal shortcut on the desktop to run this to reset unity...
```
dconf reset -f /org/compiz/
```

Finally, reload unity...
```
setsid unity
```

If unity fails to reload, logout via terminal
```
kill -9 -1
```
and log back in.

**PS:** You can't use Emerald window decorations with Ubuntu 14.04 because 
the compiz unity plugin now draws decorations.
So if you enable the decorations plugin ccsm will prompt you to disable unity.
No unity no interface.
If you want to use Emerald you would have to install the flashback session where unity is not used.
Doesn't hurt to install anyway as it will give you another session to log into when you mess up compiz.
```
sudo apt-get install gnome-session-flashback
```
This gives you 2 more login choices using the old style gnome-panel and a choice of window managers...
[LIST]
[*]Gnome Flashback (metacity)
[*]Gnome Flashback (compiz)
[/LIST]
The compiz session in flashback has the unity plugin disabled and the Window Decoration plugin enabled.
You can use Emerald in either of these sessions.

---

### Post by an3urysm on 2015-04-04
Wow, Worked like a charm... :)
Thanks a lot buddy. Everything back to normal.

I was wondering how is the right way to install emerald theme manager.

Edit: just saw your edit. Thanks for the info...

---

### Post by an3urysm on 2015-04-04
Any similar theme manager to emerald which will work with unity ?
Or any recommendations on a good theme manager for ubuntu 14.04

---

### Post by CantankRus on 2015-04-04
> **an3urysm said:**
> Wow, Worked like a charm... :)
Thanks a lot buddy. Everything back to normal.

I was wondering how is the right way to install emerald theme manager.

Edit: just saw your edit. Thanks for the info...
No problem.
Linux/Ubuntu is continually evolving so you must use guides which state what Ubuntu release used.
Unity uses the titlebar to show application menus now, so emerald is incompatible in the Ubuntu session.
The easiest way to install themes is through a ppa.
I use the noobslab theme ppa.
To add the ppa...
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
```

Then I use [**_[COLOR="#B22222"]THIS[/COLOR]_**]("http://www.noobslab.com/p/themes-icons.html") page to look at different themes.
See one I want to try.... fire up **synaptic** and install, or as the ppa is enabled just use the "sudo apt-get install" line given on the theme page.
[ATTACH=CONFIG]261100[/ATTACH]

The mediterranean-theme pack installs a number of themes.

Install **unity-tweak-tool** to choose an installed theme.
[ATTACH=CONFIG]261101[/ATTACH]

---

### Post by an3urysm on 2015-04-04
> **CantankRus said:**
> No problem.
Linux/Ubuntu is continually evolving so you must use guides which state what Ubuntu release used.
Unity uses the titlebar to show application menus now, so emerald is incompatible in the Ubuntu session.

Any similar theme manager to emerald which will work with unity ?
Or any recommendations on a good theme manager for ubuntu 14.04

---

### Post by CantankRus on 2015-04-04
> **an3urysm said:**
> Any similar theme manager to emerald which will work with unity ?
Or any recommendations on a good theme manager for ubuntu 14.04
See edit to previous post.

---

### Post by an3urysm on 2015-04-04
> **CantankRus said:**
> See edit to previous post.

Nice... 
Thanks again.

---

### Post by CantankRus on 2015-04-05
....and lastly you can install **gtk-theme-config** for some colour tweaks which carry over through theme changes.

---

### Post by hawaii243 on 2016-01-04
Thanks for this, but... I seen to be having difficulties restoring unity after using compiz 'window decoration' 

1. Followed your steps to get terminal on desktop
2. Then plugged in commands to reset unity and kill... just logs out. Still no unity bar, toolbar, or window titles on apps
3. rebooted, same issues

---

### Post by CantankRus on 2016-01-04
Once logged in to the ubuntu session, run this command to confirm session and window manager....
```
echo -e "Session: $DESKTOP_SESSION\nDesktop: $XDG_CURRENT_DESKTOP"
```
eg
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] echo -e "Session: $DESKTOP_SESSION\nDesktop: $XDG_CURRENT_DESKTOP"**
Session: ubuntu
Desktop: Unity
```

Also use ccsm to check the unity plugin is enabled.

---

