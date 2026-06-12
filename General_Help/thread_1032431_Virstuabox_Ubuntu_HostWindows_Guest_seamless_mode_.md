---
title: "Virstuabox Ubuntu Host/Windows Guest seamless mode issue"
date: 2009-01-06
forum: General Help
---

### Post by euclidsbrother on 2009-01-06
I'm not sure if this is a bug in compiz or with Virtual box, so posting here to see if anyone else has any ideas.

Running Ubuntu 8.10 host, with VirtualBox WinXP guest.

Seamless mode with ubuntu destop effects set to None.  Everything works fine.  The problems mentiond below do not happen when desktop effects are off.

Seamless mode with ubuntu destop effects set to Normal or higher.
Everything works fine as long as at least one window is open in the guest (ie.. startmenu is displayed or some program running).

If there are no windows open on the guest.. meaning only the guest task bar is displayed, then the screen whole screen goes wild. very segmented and can see partial images of apps that had been open but no longer running.. and lots of slanted sideways lines and white areas.  Kind like it's displaying a currupted screen buffer area. The only part of the entire screen that looks right, is the guest task bar.  But as soon as you click the StartMenu on the guest task bar, the whole screen corrects itself..

Anyone have a clue why they conflict like this?

Thanks
-EB

---

### Post by euclidsbrother on 2009-01-14
hmm.. this problem doesn't occur with Vista guest. I can have my desktop effects a Vista too!..  but damn vista is slow in vbox..  for now, i just keep an app, like minesweeper running on XP down in the corner..  As long as one window is open on XP, then the problem doesn't occur.

---

### Post by RingoP on 2009-01-28
I have this problem too. And I've set it up for one other person in our office who now has the same problem.

---

### Post by detrate on 2009-01-29
I had [the same problem](http://ubuntuforums.org/showthread.php?t=1047565).  Turns out it's because I have dual monitors and was trying to do seamless on my secondary.

---

### Post by niteshifter on 2009-01-29
Hi,

Known bug with post 1.5.4 VB, not an Ubuntu bug. Lots of people have this (seamless doesn't work / screen goes nuts unless one Windows window open). Popular hack: create a 1x1 pixel window (via Visual Basic, VC, etc) and have windows pop it on startup.

Showed up for me at 1.6.6. I just open a Windows window, then go seamless. But mostly I just go full screen and plop that VM instance on another desktop.

---

