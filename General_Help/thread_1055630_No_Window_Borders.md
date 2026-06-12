---
title: "No Window Borders"
date: 2009-01-30
forum: General Help
---

### Post by Ralex1098 on 2009-01-30
I'm sure you've all heard this before, but I seem to have a badass case of it. I had AWN, Emerald, and Compiz all working well when I lost my window borders. As of now, the only way for me to have window borders is to have no effects on. Normal effects results in a loss of window borders.

I uninstalled Emerald and AWN. I only have compiz and can't determine what the problem is. Any ideas?

---

### Post by N4zgu1 on 2009-01-30
have you tried compiz from the shames repo???????????

i had the same problem when  i had dreamlinux and it worked fine

---

### Post by earthpigg on 2009-01-31
'window decorations', iirc, is the compiz setting that you need to modify to get that stuff back ;)

---

### Post by thestig_992 on 2009-01-31
sometimes using emerald --replace will replace emerald (or mayber emerald --switch, you better read the help page (emerald --help))

if this works then adding to the session will run the command every time you log in

---

### Post by jimmyhacker on 2009-01-31
if you have compiz working (such as transparent panel and shading) just type emerald in console.but if you not have,type compiz-manager --replace

---

### Post by toddness on 2009-01-31
I have this problem occasionally. I installed Compiz Fusion Icon ("fusion-icon"). Clicking "Reload Window Manager" is a fast way to fix this problem. (Reloading is also good when Compiz starts to use a lot of RAM)

---

### Post by Ralex1098 on 2009-02-01
Alright, the problem is now a little different. I have window borders again, but not for firefox. I tried uninstalling and reinstalling it, but to no avail.

---

### Post by Darwinfish on 2009-02-01
Same problem any ideas?

---

### Post by MRRT on 2009-02-03
I used to have the same problem. I have fixed it by installing compiz fusion icon ( package fusion-icon on Synaptic). Once you have installed it on the menu applications will appear a new group "System" with the shortcut to the icon. Pressing it the icon will appear on the panel, right-click on the icon and one of the options that shows is "Select window decorator", a sub menu will appear with the options GTK window decorator and Emerald select the last and it should be fixed.
I remind you that emerald on ubuntu repositorie doesn't come with any window decoration, so you have to get them first, on Gnome-look for instance.

I hope it help.

---

