---
title: "[SOLVED] I can't see my whole Login Screen!!"
date: 2008-04-25
forum: Desktop Environments
---

### Post by niyonk on 2008-04-25
Hello, fellow Ubuntians :biggrin:
-First this is me first post :tongue:
-Second, am having trouble with Hardy. :frown:
 my ONLY problem so far is my Login Screen.
 It is only showing the logo and the username and password.
 The attachment below gives you an idea on how it looks like. 
 Where is the rest?? :confused:

ANY SUGGESTIONS??   :roll:
Thanks!

---

### Post by ComputerExpertVK on 2008-04-25
i have that problem too

---

### Post by Sendervictorius on 2008-04-26
You may have configured a virtual screen which is larger than your physical screen. It sometimes happens if you use nvidia tools to automatically configure your xorg.conf

If this is the case, then in /etc/X11/xorg.conf there will be a line in Section "Screen" that looks something like this:

>       Virtual     1920 1200

You can edit xorg.conf and commenting this line out. (good practice to save a copy of xorg.conf first). Then restart X (alt-ctrl-backspace)

---

### Post by ComputerExpertVK on 2008-04-26
it says i don't have the permissions to save the file...
what should i do now?

---

### Post by spacefreak86 on 2008-04-26
Open the folder as root, then open the file. Or from command line,

```
sudo kate
```

My log-on screen is at the wrong resolution, of 640 x 800. I don't know what the exact resolution for a laptop should be, but I'm guessing around 1024×768. Also, how do I go about changing it for Kubuntu?

---

### Post by ComputerExpertVK on 2008-04-26
how do you open a file from root?

---

### Post by ComputerExpertVK on 2008-04-28
thanks for helping me fix it...
however...
i used sudo nano /etc/X11/xorg.conf to do it

---

### Post by niyonk on 2008-05-06
Sorry guys, i have been offline for a while.
Anyway i decided to do a CLEAN install instead of an UPGRADE.
I will have a more stable OS :biggrin: 
Incase i get the same problem , am goin to refer to ur replies 8)
Thanks again. ):P

---

### Post by niyonk on 2008-05-06
how do you mark ur thread as solved tho? :-k

---

