---
title: "Add service to nautilus"
date: 2007-08-29
forum: Desktop Environments
---

### Post by tekkenlord on 2007-08-29
Hi,.is there a way to add a service to nautilus? For example when right-clicking I want to have the option to ps2pdf (convert postscript to pdf) option.

---

### Post by ayoli on 2007-08-29
you may want to try that: [http://gnomefiles.org/app.php/Nautilus-actions](http://gnomefiles.org/app.php/Nautilus-actions)

---

### Post by wjp.reg on 2007-08-29
> **tekkenlord said:**
> Hi,.is there a way to add a service to nautilus? For example when right-clicking I want to have the option to ps2pdf (convert postscript to pdf) option.

search for nautilus-actions and nautilus extensions

---

### Post by tekkenlord on 2007-08-29
Allright, I will try both and post again. Thanks!

---

### Post by tekkenlord on 2007-08-29
Well, I installed the nautilus-action and I got a service every time I right clicked on a postscript file. I edited it as:

Path: /usr/bin/ps2pdf
Parameter: %s

and the conditions are 

Filenames: *
(not *.ps because most of my postscipts do not have the ps extension)

However, when I select it, it returns an empty pdf file. (If I try it with the command line it works so there is no problem with my postscript file).

Any ideas? thanks!

---

