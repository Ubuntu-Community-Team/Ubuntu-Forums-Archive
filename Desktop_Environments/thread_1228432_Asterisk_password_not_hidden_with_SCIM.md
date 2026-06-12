---
title: "Asterisk password not hidden with SCIM"
date: 2009-07-31
forum: Desktop Environments
---

### Post by buixuanduong1983 on 2009-07-31
Hi everybody, I think this is a bug with the program which need administrator right with SCIM, but I cannot find any previous report.

To reproduce the problem:
- select an input method of SCIM (left-click SCIM icon on taskbar, select another input method, like Other - RAW CODE)
- open up Terminal, type in a command which need administrator password, like 'sudo -i'
- you will be asked for administrator password, type in
- the password will be shown, instead of being hidden as normal.

You may need to right-click on Terminal, select SCIM input method to show SCIM icon on taskbar.

This also happen when you open a GUI application which need admin password, like Synaptic, when all screen becomes gray with a box asking for admin password, then the password you type in will be shown.

So is this a bug, or a normal behaviour?

---

### Post by buixuanduong1983 on 2009-08-05
bump.

---

### Post by Zorael on 2009-08-06
Certainly sounds like a bug, but I can't reproduce it with my setup. I use SCIM with the Skim panel to toggle input between direct ("European/English" I believe it's called) and Anthy (Japanese).

With direct input characters appear as I type them, and they're properly hidden/disguised in password fields.

With Anthy I have to commit segments as I type, picking the context of the syllables I entered (since Japanese is chock-full of homonyms), and then they don't end up hidden.

---

