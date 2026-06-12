---
title: "No graphical login screen after i messed with ati drivers"
date: 2007-11-08
forum: Desktop Environments
---

### Post by jeppex on 2007-11-08
Well
Yesterday i wanted to try out my newly found s-video-to-scart-cable. I did so only to find to my dissatisfaction that my secondary screen was black/white. After rebooting hoping this would do anything to the problem, my screen resolution to my primary screen was way off. So I messed around a bit more with the drivers both in 'Screens and graphics' and in 'restricted drivers management' which resulted in a non-grapical login screen, and after login still a non-grapical environment, leaving me there alone with that empty command line.

The driver I ended with when the graphics broke was, I believe, ati-radeon (vesa) opensource driver.

Im now running mandriva one from a live-cd, which wont allow me to access my storage partition (where all my study-notes are) so any help would be madly appreciated.

Jeppe

OS: Gutsy Gibbon
Graphics c.: ati radeon mobility x300(not sure 'bout the last digits)

---

### Post by jjosh2004 on 2007-11-08
After you login on the command prompt, try running

```
startx
```

If the graphical environment comes up then, it could be a configuration problem in your xorg.conf causing it to fail.  If it comes up after a startx, try running

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If startx above doesn't work, what is the error message you get when you run startx?

---

