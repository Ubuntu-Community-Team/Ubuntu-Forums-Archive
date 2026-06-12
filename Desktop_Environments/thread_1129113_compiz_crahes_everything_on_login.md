---
title: "compiz crahes everything on login"
date: 2009-04-18
forum: Desktop Environments
---

### Post by Mike.lifeguard on 2009-04-18
After fiddling with some settings in compizconfig-settings-manager, I get a corrupted display on login & crash back to the login screen within a few seconds. I have to use a terminal to kill compiz before I can continue login. This is despite that I did get it working using compiz --replace in the middle of a session.

On login I see the desktop, and my mouse. After ~1s (I assume now compiz is loading) the display goes mostly black, with outlines of windows about 1 pixel wide, outlines of the panels, outlines of any menus I open, and my mouse is mostly fine (rendered very poorly, and choppy movement, but recognizable). After a few seconds of this, crash back to login screen.

I've attached a .txt with output of:
*compiz --version
*X -version
*cat /var/log/Xorg.0.log | grep intel_drv.so -C 2
*glxinfo
and my /etc/X11/xorg.conf

mikelifeguard@mikelifeguard-laptop:~$ ./compiz-check

Gathering information about your system...

Distribution: Ubuntu 8.10
Desktop environment: GNOME
Graphics chip: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
Driver in use: intel
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [ OK ]

---

### Post by Mike.lifeguard on 2009-04-18
OK, even worse now. I had to remove compiz entirely to have reliable logins, but compiz was still listed as the window manager. Since metacity wasn't running, I started it in a screen, then changed that back to metacity.

So now I can at least log in, but I don't have any visual effects, since there is no compiz to do them. There is no reason I can find that compiz shouldn't work perfectly on this system (and in fact, it did work correctly for a time), so help tracking that down & fixing it would be lovely.

---

### Post by Mike.lifeguard on 2009-04-18
Well, I re-installed compiz and it seems to be working now - both with 'compiz --replace' and on login. So... I guess this is "solved" in the sense that I don't have issues and "unsolved" in the sense that nothing was ever really solved :\

---

### Post by Mike.lifeguard on 2009-04-19
> **Mike.lifeguard said:**
> Well, I re-installed compiz and it seems to be working now - both with 'compiz --replace' and on login. So... I guess this is "solved" in the sense that I don't have issues and "unsolved" in the sense that nothing was ever really solved :\

Well, I spoke too soon. Logged out, logged back in and we're back to the beginning - except this time I don't get kicked out. So I could open a terminal and 'metacity --replace'

---

