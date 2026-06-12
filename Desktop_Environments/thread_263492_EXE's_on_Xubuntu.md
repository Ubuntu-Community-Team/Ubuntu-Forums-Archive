---
title: "EXE's on Xubuntu"
date: 2006-09-23
forum: Desktop Environments
---

### Post by heydabop on 2006-09-23
Is it possiblt to run an EXE on Xubuntu? I've tried double clicking it and right clicking a selecting execute, but from my knowledge, nothing happens. Am I just trying to do an impossible thing?

---

### Post by BLTicklemonster on 2006-09-23
You need to install wine, then you can run exe files. If I'm not mistaken it's in synaptic, make sure once it's installed, you type 

winecfg


in terminal and set up, paying attention to the tabs for devices so all your drives and such are recognized.

Hope this helps, I don't know much about xubuntu.

---

### Post by heydabop on 2006-09-23
Ok, I'll try it.

---

### Post by heydabop on 2006-09-23
What category would it be under, because I can't find it. What does synaptic call it?

---

### Post by BLTicklemonster on 2006-09-23
Look at my sig, there's the best way to install wine. It will take a while, but it's pretty full featured, not the simple sudo install wine type install. Of course its the wine tools that gives you the most stuff, so I'd be sure to go over that.

---

### Post by heydabop on 2006-09-23
Thanks. I'm going to try it right after this post.

---

### Post by heydabop on 2006-09-23
Ok, I installed wine but when I double click or right click and select execute on an .exe, nothing happens. Now wht do I do?

---

### Post by heydabop on 2006-09-23
Is there a special way to tell wine to open an .exe?

---

### Post by andiii on 2006-09-23
Terminal: wine xyz.exe

Nautilus: right-click, open with.. then select wine to open .exe files

---

### Post by MetalMusicAddict on 2006-09-23
You do realize that your trying to run a application thats  built for windows on linux right?

---

### Post by heydabop on 2006-09-23
Yes, I'm aware. Where would wine be, because I don't think it's automaticly on the list.

---

### Post by andiii on 2006-09-24
in a terminal type: "which wine"

---

### Post by heydabop on 2006-09-24
Alright I got it, I just right click selected open with another program (or whatever it says), then I browsed, found a program in the bin folder titled wine, so I tried that an it worked. Thanks a lot to everyone who helped.

---

### Post by BLTicklemonster on 2006-09-24
Woo hoo! Glad it worked! Now I used to know the command in terminal to get into wine and look around in a browser where I could see everything, but I can't remember it. I wonder if anyone else knows?

---

### Post by heydabop on 2006-09-24
That would be cool, but the fact that it works is great anyway. Thanks again.

---

