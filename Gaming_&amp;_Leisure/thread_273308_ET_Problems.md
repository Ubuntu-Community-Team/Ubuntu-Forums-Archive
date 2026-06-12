---
title: "ET Problems"
date: 2006-10-07
forum: Gaming &amp; Leisure
---

### Post by PPAAUULL on 2006-10-07
I just did a fresh Ubuntu install and tryed to get ET installed but when I start it I can get sound but the screen is black and I can't see anything. Anyone have the same problem? How can I fix it???

Thanks for the help!!!

---

### Post by jdunn on 2006-10-07
The game is running at a resolution that your monitor doesn't support.  Change your monitor settings in your xorg.config file or change the game resolution in your /home/user/.etwolf directory.

---

### Post by PPAAUULL on 2006-10-07
ok I will try that.

---

### Post by PPAAUULL on 2006-10-07
The ET config file does not have the screen res in it

---

### Post by jdunn on 2006-10-08
Assuming the problem is screen resolution, run the game and press ALT+ENTER to switch the game to windowed mode.  Then, if you can see the game, change game resolution in the "Options" menu and rerun the game fullscreen.

Sorry about your dilema.  I'm running out of ideas.

---

### Post by PPAAUULL on 2006-10-08
I will try it

---

### Post by PPAAUULL on 2006-10-08
I will tell you one thing about the last time I had it running I also installed AIGLX with Compiz and it worked fine. but since the fresh install with no AIGLX and no Compiz it won't work. I don't know if that helps much but I remember editing my xorg config file during the process.

Thanks for the help.

---

### Post by jdunn on 2006-10-08
That's odd...I would expect a 3D desktop manager like Compiz to potentially cause problems with games

---

