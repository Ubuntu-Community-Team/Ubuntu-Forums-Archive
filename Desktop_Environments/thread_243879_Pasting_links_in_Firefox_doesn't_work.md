---
title: "Pasting links in Firefox doesn't work"
date: 2006-08-25
forum: Desktop Environments
---

### Post by pinkunicorn on 2006-08-25
In most installations I've seen of Mozilla or Firefox, it is possible to paste (middle-click) a link anywhere in the browser window to get that link to open. That's a function that I like. After upgrading to Dapper, I'm no longer able to get that to work.

I can't find anything in the Firefox settings that looks even remotely relevant. How can I fix this so that I can paste links again?

---

### Post by orb9220 on 2006-08-25
I don't know if it is what you mean but when I middle click a link like on the forum here it opens in a new tab.

---

### Post by pinkunicorn on 2006-08-25
> **orb9220 said:**
> I don't know if it is what you mean but when I middle click a link like on the forum here it opens in a new tab.

If I middle-click *on*a*link* then I get a new tab, and that's what I want.

If I middle-click somewhere else (and have a link in the clipboard), then I want that link to be loaded.

---

### Post by aysiu on 2006-08-25
Are you familiar with *about:config*? I turned mine to *false* because I hate that behavior, but since you like it, you shoudl turn it to *true*.

---

### Post by pinkunicorn on 2006-08-25
> **aysiu said:**
> Are you familiar with *about:config*? I turned mine to *false* because I hate that behavior, but since you like it, you shoudl turn it to *true*.

I already had that set to true, but two lines above that I found middlemouse.contentLoadURL. After setting that to true everything works great again. Thanks!

---

