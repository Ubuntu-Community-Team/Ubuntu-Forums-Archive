---
title: "How do you delete standard emblems in nautilus?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by HanZo on 2005-10-25
I have been looking everywhere but I can't find any answers... I really like the emblems function in nautilus, but most of them are pretty useless for me (like the cvs ones, since I'm no developer). I'd like to add my own ones (and this I know how to do) and delete some of the standard ones instead... but I cannot find a way to do it... is there one? or is there at least a good workaround?
Any suggestion is greatly appreciated!

---

### Post by fabiand on 2005-10-27
Hey

"Copy 32x32 pixel PNG or SVG graphics into ~/.nautilus/emblems/ or click the Add new emblem button in the Edit->Backgrounds and Emblems dialog box."
-- [http://lintellect.org/index.php?m=200407](http://lintellect.org/index.php?m=200407)

- fabiand

---

### Post by HanZo on 2005-10-28
thanks for your answer, unfortunately this desn't solve my problem, as I already knew this. What I wanted to know was if and how i could delete the "preset" ones. It's just that it would make my life easier not to have 30 of 40 emblems I never use and make the search for the ones I want a lot longer...
anyway thanks for the link... it proved to be really useful for some other things!

---

### Post by el toro on 2005-10-28
The standard emblems are part of the default gnome theme, so going into /usr/share/icons/gnome/48x48/emblems and removing the emblems and their .icon files should make them disappear, if that's what you're looking to do.

---

### Post by HanZo on 2005-10-28
yep! will try that... hope it works.
thanks.
 edit: tried it... does not seem to work. I restarted nautilus... but still nothing. I looked for something related to it in gconf but nothing (as far as I could tell)

---

### Post by poptones on 2005-10-28
To "delete" trhose emblems you would have to remove them completely from the system, and they appear in many places. 

But you can *replace* them easily by simply installing a new theme. If you create (or copy) a theme with an emblems folder you can specify your own emblems (does it really matter what they are called so long as the icon has meaning?). 

You can also do this via an iconrc file. If you install a fairly complete theme it will have the requisite folders in place and you can see how this file works. If you do this properly you won't even have to restart gnome, just select your theme with theme manager.

---

### Post by HanZo on 2005-11-03
[QUOTE=poptones]
You can also do this via an iconrc file. If you install a fairly complete theme it will have the requisite folders in place and you can see how this file works. If you do this properly you won't even have to restart gnome, just select your theme with theme manager.[/QUOTE]

hmm... I'll try this! thanks!

---

