---
title: "force reload unity bar"
date: 2011-05-11
forum: Desktop Environments
---

### Post by kuntau on 2011-05-11
hi i have this problem with unity bar messed up. I want to know if there is some command to use to force reload the unity stuff without restarting the computer.

Something like ```
unity --reset
``` but without reset. Attached here is how unity bar messed up when I change setting in compiz manager.

---

### Post by Krytarik on 2011-05-11
You can either just relogin or restart Compiz by running this command through the Alt+F2 dialog:
```
compiz --replace
```
Greetings.

---

### Post by kuntau on 2011-05-11
Hey thx @Krytarik for the tips.. I wouldn't know that :D

---

### Post by kostkon on 2011-05-11
You can also try
```
setsid unity
```

---

### Post by kuntau on 2011-05-11
> **kostkon said:**
> You can also try
```
setsid unity
```

thx @kostkon will try that too. I'm on windows right now.. kinda frustrated by that stupid artifact (if you see my screenshot) thing.. I wonder what cause that? ATI card?

---

### Post by Krytarik on 2011-05-11
> **kuntau said:**
> kinda frustrated by that stupid artifact (if you see my screenshot) thing.. I wonder what cause that? ATI card?
It's like yourself said. When you modify certain settings in CCSM, Unity/Compiz can become glitchy, but it should get fixed if you at least restart Compiz.

---

### Post by kuntau on 2011-05-11
> **Krytarik said:**
> It's like yourself said. When you modify certain settings in CCSM, Unity/Compiz can become glitchy, but it should get fixed if you at least restart Compiz.

so thats mean everyone else also experiencing that glitch? not my specific problems? good to hear that :D

Anyway ATI card still buggy with natty.. flicker here and there~

---

### Post by Blaze08 on 2011-06-19
please help me. I tried to use the 3d cube of compiz but everytime I click the desktop cube the screen becomes absolutely nothing. Only the wall paper can be seen even I restart my pc it still shows only the wallpaper after i log in

---

### Post by wildmanne39 on 2011-06-20
> **Blaze08 said:**
> please help me. I tried to use the 3d cube of compiz but everytime I click the desktop cube the screen becomes absolutely nothing. Only the wall paper can be seen even I restart my pc it still shows only the wallpaper after i log inHi look in my signature it says reset unity and compiz, reset unity and it will fix it up.
To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.

---

