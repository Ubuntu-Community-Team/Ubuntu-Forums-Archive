---
title: "gtkpod and amarok"
date: 2005-11-22
forum: Desktop Environments
---

### Post by shadow07 on 2005-11-22
How can I change gtkpod to use amarok instead of xmms?

---

### Post by kperkins on 2005-11-23
Go to Edit > Preferences > Tools change "Command for 'play now'" and Command for 'Enqueue'" from xmms to amarok.

---

### Post by shadow07 on 2005-11-23
[QUOTE=kperkins]Go to Edit > Preferences > Tools change "Command for 'play now'" and Command for 'Enqueue'" from xmms to amarok.[/QUOTE]

Yes, I do know where to change it.  I should have been more specific.

Is there a different arguement in order to pass the audio file to amarok?  For instance, to enque a song, the arguements for xmms are "-e %s."  I would assume this would be different for amarok.

---

### Post by kperkins on 2005-11-23
"amarok %s" to play a song
"amarok -e %s" to enqueue one
%s == song you click to play or enqueue (the song chosen at the moment)
 -e is the enqueue commandline option in both amarok and xmms

---

### Post by shadow07 on 2005-11-24
Thank you.

---

