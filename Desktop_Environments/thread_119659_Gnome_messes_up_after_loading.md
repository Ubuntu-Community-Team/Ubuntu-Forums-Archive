---
title: "Gnome messes up after loading"
date: 2006-01-20
forum: Desktop Environments
---

### Post by chandler on 2006-01-20
I tried to click a theme with a question mark in the themes part..  the windows immediately turned the same shade as the top and bottom bars.  eventually everything disappeared.  Is there a file I can edit to make a different theme load by default?  doesn't go away with restarting, have to boot in recovery mode for gnome to work.

---

### Post by dcstar on 2006-01-20
[QUOTE=chandler]I tried to click a theme with a question mark in the themes part..  the windows immediately turned the same shade as the top and bottom bars.  eventually everything disappeared.  Is there a file I can edit to make a different theme load by default?  doesn't go away with restarting, have to boot in recovery mode for gnome to work.[/QUOTE]
Open Nautilus, in the Location put:

themes:///

and double-click the Theme you want to use.

---

### Post by chandler on 2006-01-20
i can only login as root (via recovery), won't this only change the root user and not my default account?

---

### Post by kuriharu on 2006-01-20
I'm with Chandler on this...I changed themes and my login screen, now Nautilus won't run. I just get the yellow/brown screen with a mouse pointer and nothing runs. I also have to run recovery console.

Is there a way to change the default gnome theme and maybe login screen?

---

### Post by chandler on 2006-01-20
I pretty much got it to work, but had to redo all my settings... what i did was I just went to users and groups under System > Admin, then I made a new user with admin abilities, then I just deleted the other account.  then I log in with the new account

---

