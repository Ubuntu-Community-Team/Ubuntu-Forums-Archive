---
title: "firefox segfault"
date: 2005-04-27
forum: Desktop Environments
---

### Post by souki on 2005-04-27
hello,

I'm using hoary + mozilla-firefox 1.0.2-0ubuntu5
I have a very strange segfault with firefox when accessing some textareas
I can reproduce the segfault on a specific html page

steps:
1- save the attached file "ff-segfault.txt" to "ff-segfault.html"
2- open the saved file with firefox
3- place the cursor anywhere on the text in one of the textarea
4- use the arrow key (left or right) to move the cursor

As soon as I press the arrow key, firefox exits with segfault
I can reproduce this with a fresh profile

could someone try this file?

thanks for any help
~souki

---

### Post by syltty on 2005-04-27
crashed also my box: pentium III on hoary + mozilla-firefox 1.0.2-0ubuntu5

---

### Post by shakin on 2005-04-27
There's a backport for 1.0.3. Why not upgrade and see if that fixes your problem?

---

### Post by souki on 2005-04-27
[QUOTE=shakin]There's a backport for 1.0.3. Why not upgrade and see if that fixes your problem?[/QUOTE]

have you tested the attached file?
If it does not segfault I will use the backport

---

### Post by souki on 2005-04-27
The backport doesn't work :(

I have tested several versions, and it seems that it is an ubuntu specific problem:

- mozilla-firefox 1.0.2-0ubuntu5 : segfault
- mozilla-firefox 1.0.3-2~5.04ubp1+1.0.2-0ubuntu5 : segfault
- mozilla-firefox 1.0.2 official : works
- mozilla-firefox 1.0.3 official : works

I've also tested without the mozilla-firefox-gnome-support package

---

