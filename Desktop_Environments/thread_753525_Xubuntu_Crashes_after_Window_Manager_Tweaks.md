---
title: "Xubuntu Crashes after Window Manager Tweaks"
date: 2008-04-12
forum: Desktop Environments
---

### Post by Guitar John on 2008-04-12
Ok, so after installing Xubuntu on my old Dell 3500 (now belongs to my sister-in-law), I was seeing how things worked with Xfce.  I'm used to Gnome on my computers.  FWIW, the specs are Celeron 366MHz, 256 MB, 60 GB HDD (upgrade).

So I try Applications > Settings > Settings Manager > Window Manager Tweaks after seeing this [YouTube video]("http://www.youtube.com/watch?v=1iOwruZMXGc").  I ticked the box for "Enable Display Compositing" and ....*poof*.....I'm looking at a blank screen.  

I can still get to my desktop using the method described in my post in [this thread]("http://ubuntuforums.org/showthread.php?t=743639").  
> **Guitar John said:**
> My problem seems to be a little more difficult.  The only way I can get everything back is to log into "Failsafe Terminal" or something like that. Then type into the terminal ```
xfce4-panel
```

 Then following AstalaVista's instructions:


This does bring back the desktop and background picture.

The problem is that I cannot logout.  My only option is "Exit Xfce Panel.  

When I do that, it only exits the panel, it doesn't Restart, Shut-Down or anything else.  If I shut off the computer using the power button, I'm back to square one.  

Any ideas?

EDIT:  I enabled Right click menu, and went to "Quit".  I got:
```
**Unable to quit session**

Quitting the session requires that Xfce's session manager
 (xfce-session) is running, but it was not detected.  Please 
quit Xfce via another means.
```


Hopefully there is a solution other than re-install.

---

### Post by sardion on 2008-04-13
So I don't have xubuntu anymore, but I can try to help:

When you changed the settings in Window Manager Tweaks, you actually were changing the contents of a file.  It's one of the files in /home/YOURUSER/.xfce/
Unfortunatley I don't remeber which.

You can look through them by hand, or you can remove that whole directory ... but that will *delete* all your xfce settings and reset them to default.

The best thing I can tell you is to do this:

mv .xfce   xfce-save

(move the dir)

then reboot, you will be in a default xfce enviroment.

move the files in you xfce-save dir back one at a time until you find the one breaking things, then delete that one.

---

### Post by Guitar John on 2008-04-13
With "Show Hidden Files" checked, there was no file or folder by that name.  I typed ```
 whereis .xfce
``` ito the terminal and it returned ```
.xfce
```...

...great, a computer with an attitude.  [-X

Since this was a new install on which I had only begun setting up, I wound up backing up the few files I had on the computer (onto a 1GB thumb drive) and re-installing.  

Not the best solution, but it'll work.  I was actually going to wait until the release of 8.04 and do a clean install then, but I wanted to see what I was getting myself into.

Translation:  I couldn't wait.

Thank you sardion, for your input.

---

