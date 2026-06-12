---
title: "Oh no! I borked my Ubuntu install.."
date: 2005-12-19
forum: Desktop Environments
---

### Post by three_sixteen on 2005-12-19
So, I'm sure you can tell from my post count that I'm new to both ubuntu and linux in general.  

I managed to mount my windows partition and change my theme and whatnot off of the bat, but then started reading about e17 and thought I would give it a shot.

Well, GDM won't start now because something with the e17 install didn't work. Should I just reinstall Ubuntu or is there an easy way to fix this?

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=three_sixteen]So, I'm sure you can tell from my post count that I'm new to both ubuntu and linux in general.  

I managed to mount my windows partition and change my theme and whatnot off of the bat, but then started reading about e17 and thought I would give it a shot.

Well, GDM won't start now because something with the e17 install didn't work. Should I just reinstall Ubuntu or is there an easy way to fix this?[/QUOTE]
From the terminal, you could try:
```

$ sudo dpkg-reconfigure gdm

```

---

### Post by anil_robo on 2005-12-19
This option of reconfiguring gdm should be there at the login screen as a button, which noobs can click just in case something goes wrong! :D

---

### Post by three_sixteen on 2005-12-19
[QUOTE=anil_robo]This option of reconfiguring gdm should be there at the login screen as a button, which noobs can click just in case something goes wrong! :D[/QUOTE]

Weee, fun times.

I actually just ended up formatting the partition and reinstalling it on a bigger partition anyways. 

Thanks for the help though, I'll keep this in mind next time I decide to play with something :)

---

### Post by stalefries on 2005-12-19
Good idea. As far as I know, E17 is still in devel. You might want to avoid running anything that isn't in the repositories, unless you have a good reason to do so.

---

### Post by az on 2005-12-19
[QUOTE=three_sixteen] Should I just reinstall Ubuntu or is there an easy way to fix this?[/QUOTE]

Easy fix.

---

