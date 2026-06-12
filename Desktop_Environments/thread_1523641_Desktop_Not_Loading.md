---
title: "Desktop Not Loading"
date: 2010-07-03
forum: Desktop Environments
---

### Post by Sirnot1 on 2010-07-03
Hey all!


Ive recently installed Ubuntu 9.10 on a 2.0 GHz Gateway computer (circa 2004) and have been having issuses with loading the desktop.

When the desktop would load on ever boot, it would load part of GNOME, and the cursor, but thats all... The background is black, and it does not respond when you click on anything. No icons, not all of gnome loaded. What should i do?

---

### Post by wojox on 2010-07-04
Did you try running a Live CD before you installed to see if everything worked out okay?

---

### Post by Sirnot1 on 2010-07-04
Yep, all was fine...

---

### Post by gunfyter on 2010-07-04
Do me a favor.   I am nt sure i understand exactly what you are describing....

I had a problem with the desktop not loading...

I went to the terminal Ctrl-Alt-T

**sudo apt-get install ubuntu-desktop**

did the trick for me.      I don't remember if I had to reboot after that.

---

### Post by lkjoel on 2010-07-04
Log into xterm, then download LinuxEssentials from my sig.
Extract it then type in a terminal:
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```That will load GNOME.
And If you have Terminal Enhancements 0.2 (from my sig) installed, you only need to type:
```
chmod +x FASTGNOME.sh
FASTGNOME.sh
```

---

### Post by Sirnot1 on 2010-07-05
ill try both replies.

---

### Post by alenn on 2010-07-05
I had the same problem and I set graffic on low and then it was fine.

---

### Post by clb199 on 2010-07-06
I had the same problem, fix was reset the display to 1028 x 764. Resolution was too high.

---

