---
title: "Configuring keyboard in xfce"
date: 2006-02-13
forum: Desktop Environments
---

### Post by Elvish Legion on 2006-02-13
Well I just noticed print screen won't take a screen shot, and unlike gnome I can't seem to find the key configuration (i found a keyboard set up but not keys)

Any help? Is there an easier way to screen shot in xfce? Oh and I just noticed that sypantic doesn't seem to have the most up to date xfce packages...can I add them? I don't like to compile things by hand if I can avoid it....I'm worried I'll break something

---

### Post by PapaWiskas on 2006-02-14
Open a terminal and type

import -window home/whateveryourusernameishere foo.jpg 

(.jpg can be changed to .png if you prefer)

This will bring up a + symbol cursor thingy....and you can either click on an empty spot of your desktop to get a whole desktop shot or click on individual windows to get a shot of just that window.

Or if you have scrot installed you can do a keyboard binding...
As long as you have scrot installed this should work

to do a  binding with scrot, 

scrot '%Y-%m-%d_$wx$h.png' -e 'mv $f ~/' 

to get a keybind for snapshots.

---

