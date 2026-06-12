---
title: "Windows stuck to position 0x0."
date: 2008-12-17
forum: General Help
---

### Post by ediblespread on 2008-12-17
Hey guys,

Relatively new to Linux, and Ubuntu, so was playing with desktop effects the other day, and ran across a guide on how to get a terminal embedded in your desktop. Now, I normally use devilspie to do this, but it isnt perfect; I still cant get it to fullscreen the terminal unless I do it manually (I have a 1680x1050 res, so full screening it would be nice ¬_¬) and it also still appears in the taskbar. So, ran across this guide that told me how to do it without using devilspie, and promised to make it full screen too.

Long story short, it involved editing a few things in the CompizConfig settings, such as auto-window placement to the position 0x0, APPARENTLY for just the console (using title=[title]). However, it didnt work out too well so I started to remove the effects, turning off the various options. Of course, it couldnt be that easy - now, whenever I launch ANY program, it automatically reverts to the 0x0 positon, which of course means that its top-bar bit (with the minimise, maximise and close buttons) becomes hidden behind the top taskbar. Which is a pain. I cannot understand why it is doing this - all the "Window Placements" and "Window Rules" effects in CompizConfig are turned OFF...

Any ideas?

Thanks,
Ediblespread


EDIT: Sorry, this is Ubunutu 8.10 I believe - using the Wubi installer. Ta.

---

### Post by ediblespread on 2008-12-17
Ah! Fixed it. All I did was disable one effect too many - accidentally disabled the window placement manager, so instead of using smart placing it was just placing windows in the default position.

Sorry to waste space in your forum with what turned out to be such a stupid issue! ^^.

-Edibles

---

