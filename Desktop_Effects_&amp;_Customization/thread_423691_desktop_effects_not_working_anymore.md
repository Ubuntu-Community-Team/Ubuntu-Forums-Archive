---
title: "desktop effects not working anymore"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by pdrift on 2007-04-26
i installed feisty last week and i really liked the desktop effects.
well somehow i messed up my system because now i cannot see the cube anymore
i installed beryl but then i uninstalled it and now i only get the wobble effect.
for some reason i can't use the cube view that gave me 4 workspaces. 
now i only have two. i tried to re enable the effects but only wobble works.
and also i was using utorrent flawlessly but now it will not maximize.
i cannot even view what i'm downloading.  i click on the green u in my panel but 
it  dioesn't maximize and i have no access to the controls.
i hope i don't have to reinstall... again ;(

someone please help me.

---

### Post by Aetherius on 2007-04-26
the cube problem is known, try this

```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```


[https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/89786](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/89786)

---

### Post by bapoumba on 2007-04-26
@ pdrift: moved your thread to "Desktop Effects & Customization".

---

### Post by ajack on 2007-04-26
> **Aetherius said:**
> the cube problem is known, try this

```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```


[https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/89786](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/89786)

Thanks for the tip, I was searching for a quick fix to this problem... :-)

---

### Post by pdrift on 2007-04-26
hey thanks for the tip, worked like a charm. 
am i gonna have to do that for each session?

i thought this might fix my other program but i still can't maximize utorrent.
i wonder is that a graphics problem or is this a wine problem?

oh and sorry for posting in wrong forum.

---

### Post by El Viejo Lobo on 2007-04-26
Hi pdrift, keep this commands in hand. I upgraded to Feisty last night and fixed it about 3 to 4 times since I activated Compiz.
Try to not dis-activate the cube. :guitar:

---

### Post by Aetherius on 2007-04-27
its not actually a bug, it was chosen as default behaviour because compiz tends to play havoc with the gnome-pager, those two littles edits to gconf work around that by fooling gnome into thinking its one desktop, not four. you'll have to do it pretty much everytime you disable/enable compiz. A solution to this would be:.....

Fire up a terminal

> sudo nano /usr/bin/fixcompiz

then in the nano window type

```
#!/bin/bash
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```

hit ctrl+x....type 'y'.....hit enter

then type

```
sudo chmod a+x /usr/bin/fixcompiz
```

now you just type fixcompiz in any terminal to fix the problem ;)

you can also now add fixcompiz to your startup session ( System >> Prefs >> Sessions) so it runs every login

A hackish and messy way to do it, but it works

---

### Post by Kevin on 2007-04-27
You could also just install gnome-compiz-manager from the repos, as it has the ability to properly change between workspaces, the cube, and the plane, as well as other oft-used settings.

---

### Post by El Viejo Lobo on 2007-04-27
Hola Aetherius,  Thanks,  your hackish and messy way worked perfect for me. It saved the honor of the idea (Ubuntu/Compiz) when I showed it on my old PC to the Vista boys with the multi giga machines.:guitar:

---

### Post by Aetherius on 2007-04-27
not a problem, brother, as for settings managers, i prefer hackish messy scripts ;)

---

### Post by steam_engenius on 2007-04-27
Thanks a lot man, I was having trouble with this as well. :)

---

