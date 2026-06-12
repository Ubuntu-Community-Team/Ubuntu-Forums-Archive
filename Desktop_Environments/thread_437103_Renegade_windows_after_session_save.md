---
title: "Renegade windows after session save"
date: 2007-05-08
forum: Desktop Environments
---

### Post by spupy on 2007-05-08
Hey there!

I have this annoying problem. I was tinkering around with gconf-editor, changing programs settings and stuff. I checked the "save session" option for gnome-session, but later turned it off, because it thought i wasnt working. Still, ubuntu somehow "saved" my session. So now, every time i log into gnome, a gconf-editor starts up at workspace 1, and a nautilus starts at space 3! More of this: when i start programs, they sometimes dont appear on the current workspace, but randomly on other spaces. Nautilus makes this trick the most. Even more! This problem transfered to Xfce, even thou i installed xfce after all of the tinkering! Only fluxbox doesnt suffer. Im not using gnome anymore, i use fluxbox, but when i need to use gnome (for whatever reason lol), it drives me crazy!

Sorry if there is already a solution, i have abolutely no idea whats causing this!
Thanks in advance!

---

### Post by mythik on 2007-05-08
at one point, for a different reason I had to delete my session file.
> 
~/.gnome2/session 


I THINK that if you get rid of that file it will work.  I had another issue with session saving.  described here [http://ubuntuforums.org/showthread.php?t=434013](http://ubuntuforums.org/showthread.php?t=434013)

---

### Post by spupy on 2007-05-08
Well, i dont have such file at all. But i did got rid of some saved sessions in nautilus and metacity folders. I hope next time i log into gnome its ok.

---

### Post by mcduck on 2007-05-08
Just enable the 'save session', close all programs and log out. Now you have a saved session with no open programs. Then log in, and disable 'save session' again. :D

---

### Post by mythik on 2007-05-08
> **mcduck said:**
> Just enable the 'save session', close all programs and log out. Now you have a saved session with no open programs. Then log in, and disable 'save session' again. :D

I tried that before too....no luck.

I really don't think the savesession thing is really working as intended.

---

