---
title: "&quot;Add Application&quot; (Synaptic) is gone. (Solved)"
date: 2005-10-31
forum: Desktop Environments
---

### Post by ad noiseam on 2005-10-31
Hello,

All of a sudden, and without playing around with it, the "Add applications" entry in the Gnome Menu is gone. Nix, nada, no way anymore to add or remove a program without having to go to the terminal.

Is there anyway I can bring back this link from the dead?

Nicolas

---

### Post by magnusbb on 2005-10-31
Right-click on the applications menu, and fire up the Menu Editor. Maybe the entry is hidden, and that you just need to un-hide it.

---

### Post by ad noiseam on 2005-10-31
Been there, done that. The entry is not hidden, it is just not there at all.

I can still reach the "advanced" Synaptic from the terminal, and I guess something just got un-installed. Does anybody know how to get this back (maybe downloading it / installing it again)?

---

### Post by Jens Willem on 2005-10-31
I have the same problem. Suddenly, the "Add Aplication" entry in the gnome menu is gone, also form the Smeg Menu Editor.

---

### Post by jdwannam on 2005-10-31
Well I can't tell you why it happened... but try this from a terminal window.

sudo apt-get install gnome-app-install

Or just use Synaptic Package Manager if you still have that.

Good Luck,

J.D.

---

### Post by ad noiseam on 2005-11-01
This did the trick, thank you.

---

### Post by cydec on 2005-12-04
Same problem, Same solution: thanks !

---

