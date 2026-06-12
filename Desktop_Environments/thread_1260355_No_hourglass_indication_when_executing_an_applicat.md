---
title: "No hourglass indication when executing an application"
date: 2009-09-07
forum: Desktop Environments
---

### Post by majikins on 2009-09-07
Hi

I have a couple of lauchers on the desktop.  When I execute an application via these launchers, there is no indication that there is anything happening until such time as the application appears.

I have loaded new cursor themes and the themes only show mouse indication when inside an application but when I go to the window bar or to the desktop, the cursor theme defaults to just a cursor that is static.

How can I fix this?

---

### Post by majikins on 2009-09-09
bump?

---

### Post by mcduck on 2009-09-09
Have you logged out and back again after switching the cursor theme?

The cursor will immediately only change for new started applications, not the ones that are already running.

---

### Post by majikins on 2009-09-11
Ok that worked for showing the mouse pointer consistent everywhere.  But I still have the problem of no indication on the pointer when executing a launcher icon on the desktop.  I also note that when executing an application via the main menu, there is also no indication of working on opening application via a busy mouse pointer.

Never noticed before until a user pointed this out to me! I hope someone could answer/solve this!

---

### Post by majikins on 2009-09-11
Solved! Nice guy on another forum gave me the solution.  When creating the launcher, the launcher has "name.desktop" as its name attributes.  Use your favourite editer to edit this launcher file and add "StartupNotify=true" without the quotes at the end of the file. Save and exit - launch and you will see the mouse pointer change to its working sign!

Osum opensource magic!

---

