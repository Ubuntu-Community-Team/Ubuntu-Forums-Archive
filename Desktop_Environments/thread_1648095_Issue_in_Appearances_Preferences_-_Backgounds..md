---
title: "Issue in Appearances Preferences - Backgounds."
date: 2010-12-18
forum: Desktop Environments
---

### Post by lodravah on 2010-12-18
Heyall. 

So I did something stupid today and added a whole folder in backgrounds. A folder with 1200 pics. After realizing my mistake and waiting for the loading the finish, I manually removed all the pics. 

However, when I open Appearances Preferences - Backgrounds it takes forever to open and I suspect it has something to do with my mistake. It seems like the application is reloading, or at least trying to reload pics that are not there. I'm thinking that I need to clear a cache somewhere, or something like that. 

Any ideas?

---

### Post by sikander3786 on 2010-12-18
Pictures here:
/usr/share/backgrounds


Info here:
~/.gnome2/background.xml

.gnome2 is a hidden directory inside your /home. Press Ctrl + H to see it.

---

### Post by lodravah on 2010-12-18
It worked. Thanx a lot :)

---

