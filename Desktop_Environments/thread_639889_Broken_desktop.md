---
title: "Broken desktop"
date: 2007-12-13
forum: Desktop Environments
---

### Post by snakefing on 2007-12-13
Proof that a little knowledge is a dangerous thing...

I was trying to update some development libraries, and apparently I've got an inconsistent set or something. Anyway, the problem is that my desktop is broken now.

Symptoms:
When I reboot, I get an error even before the login screen comes up: There was an error loading the theme Human. Couldn't recognize the image file format for file '..../bottom_bar.svg'

I click OK, and a default login screen comes up, I can log in and it starts my desktop. The top and bottom bars appear, flash a few times, then disappear and only the desktop (background and a few icons) remain. No menu bar, task bar, etc. I can right-click to Create New Folder, etc. If I double click a folder icon, everything on the desktop vanishes (except background) and right-click no longer functions.

I've tried creating a new user, using apt-get to upgrade the distribution, and a few other things, but the problems still persist. Sudo apt-get check returns nothing.

I could try re-installing Ubuntu as a last resort, but I thought I'd see if there was a library or package I need to revert or reinstall.

---

