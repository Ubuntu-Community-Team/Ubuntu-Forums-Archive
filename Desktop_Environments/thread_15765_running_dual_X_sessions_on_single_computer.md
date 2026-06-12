---
title: "running dual X sessions on single computer"
date: 2005-02-16
forum: Desktop Environments
---

### Post by ming0 on 2005-02-16
I have 2 users that want to be logged in to the same computer and be able to instantly switch with alt+ctrl+f6/alt+ctrl+f7.

I'm not sure which file has the configuration that will enable this.

Also, would I get the 2nd session going w/ startx? 

Thanks for the help :)

---

### Post by mendicant on 2005-02-16
Applications->System Tools->New Login seems like it would do the trick.  When I tried it, it actually logged me out of my original session.  Not that I cared, but you might want to be aware of it.

---

### Post by alastair on 2005-02-16
As well as the GUI "new login" (which seemed to work for me OK the one time I tried it), you could also :

CTRL+ALT+F1
login: as whoever

run: startx -- :1

This also starts a new X session on display 1.

---

### Post by ming0 on 2005-02-16
Cool, I tried the 2nd idea, and it works great. As a side note, I just use ctrl+alt+f7 and ctrl+alt+f8 to switch between the sessions. (this way messes up the sound server, and you have to reset the server and open it depending on the desktop you're on)

Thanks  :-D

EDIT:

Actually I just tried the 1st suggestion, and it worked /w out logging my original session out.

W/ this method, you can use the sound server on either desktop, but the one that started playing the sounds first is the only one that actually makes any noise.

---

