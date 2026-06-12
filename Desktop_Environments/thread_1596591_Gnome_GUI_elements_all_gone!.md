---
title: "Gnome GUI elements all gone!"
date: 2010-10-14
forum: Desktop Environments
---

### Post by umlguy on 2010-10-14
I've got a Ubuntu instance that was running fine under 9.10 for some time.  Then I did "something", I don't remember or know what, and all the GUI components (menu bar, desktop launchers, bottom app panel) have gone away.  I then upgraded to 10.04 thinking that might fix it, but no, I'm now running 10.04 without the GUI components.  Right clicking the desktop does nothing, no context menu.  I can login with what looks like a normal login, the screen timeout seems to work, but once logged in there are no GUI components on the screen, just the desktop background.  I used alt+F2 to do the upgrade.

Help, I really don't want to rebuild the whole thing.

---

### Post by 3Miro on 2010-10-14
At least if Alt+F2 is working, then something can be done.

Try running gnome-system-monitor to see if gnome-panel is running. If it is running, then kill it. If it doesn't start by itself, try starting it manually.

Try Alt+F2 and type 
```
metacity --replace
```
This turns off the visual effects, it may have something to do with the problem.

If those don't help either, you can run gnome-terminal and then add a new user. Logout and try loggin as the new user. Here is the HOWTO on adding a new user from the terminal (the bottom of the page).
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

If the new user has working gnome, then the problem is with the settings on your system. If not, then the problem is much bigger. Post with the results on what happened.

---

