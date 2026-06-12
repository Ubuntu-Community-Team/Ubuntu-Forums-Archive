---
title: "Kmenu shortcut key re-assignment problems"
date: 2006-06-25
forum: Desktop Environments
---

### Post by SadaraX on 2006-06-25
I try to add a shortcut key (such as WIN+A) to a program in my kmenu, but it says "The key WIN+A cannot be used because it is already in use". However I have looked through all of my menu entries and nothing is using the WIN+A key, and pressing that combination does not do anything. 

Can someone help me get my menu's straightened out?

---

### Post by aysiu on 2006-06-25
Paste these commands into the terminal: ```
sudo updatedb
grep -inr "Key=Win+A" ~/.kde
``` The first command may take a while (two minutes max).

---

### Post by SadaraX on 2006-06-25
Thanks, that worked...

---

