---
title: "Can't get trash basket on desk top"
date: 2007-02-24
forum: Desktop Environments
---

### Post by Jensor on 2007-02-24
I can get a trashcan icon on the Panel at the top of the screen, but so far have not been able to get one on the desktop.

I tried this:
In terminal window:

"sudo gconf-editor"

This opened the configuration editor

Did apps> nautilus >desktop > trashcan icon visible

then I rebooteed and still no trashcan icon on the desktop.

I then went to my home folder and made hidden files visible and then created a link to .Trash, then dragged the link to the desktop. However that is not what I really want.

Does anyone know how to get the icon there. It would be nice if you could just right click on the desktop and make the appropriate selection.

Jack Ensor
Edit/Delete Message

---

### Post by Jensor on 2007-02-24
I forgot to mention I'm running Ubuntu 6.06 LTS.

Jack Ensor

---

### Post by stueyboy on 2007-02-26
If you go into the configuration editor in system tools then navigate to apps>nautilus>desktop there should be a box to check which will show the trashbox

Hope this helps

---

### Post by f3nol on 2007-02-27
Hi Jensor

I´m trying to get a trashcan on my desktop too. I´ve done this: right click on desktop>Create Launcher, and as a command I typed ´nautilus .Trash´. But it´s still not perfect, there´s no ´Empty Trash´under right mouse :( 
Let us know if you figure out something better.

---

