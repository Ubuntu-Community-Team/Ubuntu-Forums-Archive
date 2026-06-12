---
title: "Title bar icon missing"
date: 2009-03-13
forum: Desktop Environments
---

### Post by fastfret79 on 2009-03-13
Hi,

Just done a fresh install of Ubuntu Studio and after setting up all my apps I realised that the icon in the top-left of the title bar is missing for all apps. 

Ive attached a screenshot of the calculator just to show what I mean - there is no icon in the top left. 

No matter what theme, window border or anything else I choose seems to make any difference. I am using compiz, but nothing in the settings relate to this (as far as I can see) and turning compiz off has no effect either.

Anyone got any ideas?

---

### Post by fastfret79 on 2009-03-14
Eventually worked out how to fix this!!! 

First press Alt-F2 to bring up the run dialog and run 'gconf-editor'

Once open, navigate to 'Apps > Metacity > General' and change the value of 'button_layout' to 'menu:minimize,maximize,close' (mine was missing the 'menu')

---

