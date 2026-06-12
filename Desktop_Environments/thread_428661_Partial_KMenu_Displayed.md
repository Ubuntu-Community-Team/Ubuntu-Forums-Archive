---
title: "Partial KMenu Displayed"
date: 2007-04-30
forum: Desktop Environments
---

### Post by RandySavage on 2007-04-30
Running Kubuntu Feisty Fawn 7.04.  I have looked through the various forum posts as well as reviewed configuration items for system settings and menus in /etc without finding a clue as to what might be causing this.
:confused: 
Under KMenu, only a partial display of available menus & sub-menus shown.  In my case displayed under the heading "All Applications" is (top to bottom):
submenu Graphics
submenu Internet
submenu Multimedia
submenu Office
submenu System
submenu Utilities
menu Add/Remove Program
menu Find Files/Folders
menu Help
menu System Settings

But when I open Kmenu menu editor I can see those plus:
submenu Debian
submenu Edutainment
submenu Games
submenu Science & Math
submenu Settings
submenu Lost + Found

Any suggestions?

---

### Post by aysiu on 2007-04-30
Try creating a new test user.

If the test user is experiencing the same problems, it'll be more difficult to diagnose, but at least we'll know it's a system-wide problem.

If the test user doesn't experience the same problems, we know there's something wrong with your user profile.

---

### Post by RandySavage on 2007-04-30
> **aysiu said:**
> Try creating a new test user.

If the test user is experiencing the same problems, it'll be more difficult to diagnose, but at least we'll know it's a system-wide problem.

If the test user doesn't experience the same problems, we know there's something wrong with your user profile.

I created a new test user and logged in as that user and the menu issue is identical.

So, if its a global configuration item, I can surmise that there is something either specifically related to how kmenus are displayed, or there is some other configuration item, possibly even unrelated, affecting how kmenus are displayed.  I know that's pretty vague.  

I cannot see any related setting in the kmenu menu editor, although it doesn't really seem to have much that can be configured.  I'm not sure what other configuration item might affect this.

What do you think might be the next thing to review?

---

### Post by aysiu on 2007-04-30
Are these submenus empty, by chance? > But when I open Kmenu menu editor I can see those plus:
submenu Debian
submenu Edutainment
submenu Games
submenu Science & Math
submenu Settings
submenu Lost + Found In other words, when you click the + sign next to Edutainment, and expect the submenu, are there any applications within the Edutainment category?

---

### Post by RandySavage on 2007-04-30
> **aysiu said:**
> Are these submenus empty, by chance?  In other words, when you click the + sign next to Edutainment, and expect the submenu, are there any applications within the Edutainment category?

Indeed, that's the answer: they're empty.

I had previously thought they weren't empty because I saw items, but upon further inspection those items are just more empty sub-menus.

Is there any easier way of adding menu items, either for programs that already exist in /usr/bin, or for newly added programs than by hand, manually?

---

### Post by aysiu on 2007-04-30
Properly packaged programs will come with a .desktop file in /usr/share/applications or /usr/share/applications/kde. That .desktop file will contain menu entry specifications (name of the launcher command, displayed title of the program, description of the program, default icon for the menu entry).

Some packages, unfortunately, are not properly packages (i.e., they don't come with a .desktop file), so you have to create the menu entry manually.

---

### Post by Jucato on 2007-04-30
The K Menu doesn't show empty submenus. That is why there is nothing under the Debian, Edutainment, Games, Lost+Found, etc. submenus, unless you installed something that goes into those menus.

---

