---
title: "Wallpaper disappeared, just black instead, cannot change wallpaper"
date: 2008-07-29
forum: Desktop Environments
---

### Post by kavoura on 2008-07-29
I logged in as normal into Ubuntu 8.04 on my AMD64 PC, using Gnome. Usually the wallpaper is the default heron picture, but tonight I just have a black desktop, no picture at all. I tried to change the wallpaper, but whatever I select, the screen remains black.

What could have caused this and how do I get my wallpaper back?

---

### Post by alt3rn1ty on 2008-09-18
I have exactly the same problem, sorry no solution here yet, I thought I had it fixed once but the same problem keeps recurring on both my desktop and laptop (Both 8.04 x64 for AMD Athlon 3400, and both have NVidia graphics drivers (but the laptop has the old drivers for Geforce 4 compatibility).
I have installed compiz config settings manager (to access more advanced cube/desktop settings), and otherwise everythings fine, just the annoying wallpaper problem.

---

### Post by mike1234 on 2008-09-18
If you right click on your desktop, and select change desktop background, what do you see? Click on "add" and navigate to where your wallpaper is located. usr/share/backgrounds is default folder where hardy wallpapers are. Otherwise I keep wallpaper in my pictures folder in home.

M.

---

### Post by alt3rn1ty on 2008-09-19
Well when I wrote the reply post I was getting the same problem after selecting change wallpaper the dialogue came up but no matter what wallpaper selected I still had a black background. Either selecting the standard Hardy heron wallpapers or the ones in my picture folder which have been added to the selection, also doing a couple of restarts of the computer.

However, since then I have been busy and have not loaded Linux until tonight, strangely at first load the wallpaper is back again. This has happened before and I cant pin it to any particular action I have taken or as a result of any update. It just seems to be a random occurence with no particular method of resolving it permanently.

---

### Post by EvilDaemon on 2008-09-19
Maybe it was due to the power-off / reboot?

---

### Post by alt3rn1ty on 2008-09-19
As opposed to just restarting?, no idea. Will pop back in if/when it happens again.

---

### Post by mike1234 on 2008-09-19
Occasionally my 8.04 has done that ( I think twice). Rebooting fixed it. I just figured it was a compiz glitch. Selecting no desktop effects after having compiz enabled makes my screensaver start for about one second. Then it switches back to normal (no effects). 

M.

---

### Post by jan schoubo on 2008-09-27
Same problem with Ubuntu 8.04 on Dell Latitude D630 - black desktop but menus, clock etc. in the top and bottom grey bar all work fine. Switching System -> Preferences -> Appearance -> Visual Effects to None gives a light brown background, but that is the only change I can affect. I can select the Heron or a solid color in System -> Preferences -> Appearance -> Background, but still only black shows.

One curious thing too: Right-clicking within the desktop area, or dragging a box are all dysfunctional - no popup menu or rubber box being displayed. Also my mounted disks shows up in Places -> Removable Media but not on the desktop.

Is there a process responsible for the desktop graphics in general? If so, maybe that process is dead?

---

### Post by jan schoubo on 2008-09-27
Searched for GNOME-related problems rather than UBUNTU-related, and found the solution in [http://www.linuxquestions.org/questions/linux-newbie-8/gnome-desktop-icon-disappeared-27724/](http://www.linuxquestions.org/questions/linux-newbie-8/gnome-desktop-icon-disappeared-27724/)

Basically, nautilus is the process I assumed in charge, and 
killall nautilus
will cause it to go away and being restarted - and voila: Icons and Heron is back.

---

