---
title: "Problems w/ compiz fusion!"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by kris2pe on 2007-07-07
I seemed to get the same set of problems w/ Compiz fusion! The top bar which has the close, minimize, maximize are also gone! I don't know what additional command lines that are needed! 
Plus I like the fact that in beryl you can change the window themes into vista or aero. I would also like to know how to integrate it in my ubuntu!

---

### Post by tgm4883 on 2007-07-07
> **kris2pe said:**
> I seemed to get the same set of problems w/ Compiz fusion! The top bar which has the close, minimize, maximize are also gone! I don't know what additional command lines that are needed! 
Plus I like the fact that in beryl you can change the window themes into vista or aero. I would also like to know how to integrate it in my ubuntu!

You can use emerald to theme compiz fusion.  As for the other problem.

From [http://ubuntuforums.org/showthread.php?t=481615&highlight=compiz+fusion+title+bar](http://ubuntuforums.org/showthread.php?t=481615&highlight=compiz+fusion+title+bar)
> 2. No window borders!

Well actually, I think there are a million possibilities for why this happens, but everytime it happens to me I can fix it with this command. Run it with alt+f2:

Code:

emerald --replace &


Well, that's all for now, hope it works out as well for you as it did for me, best of luck!

---

### Post by redsox59 on 2007-07-13
I have run into this same problem. "emerald --replace &" does not seem to do anything.  Also my terminal only shows up as a white space on the screen.

---

### Post by bdtgp on 2007-07-13
Add this line to your device section in your xorg file:
```
Option "AddARGBGLXVisuals" "True"
```

Then run this command with Alt+F2
```
compiz --replace &
```

Let me know if that works.

---

### Post by redsox59 on 2007-07-13
Yes that was it! Thanks for the super fast reply!

---

### Post by bdtgp on 2007-07-13
No problem. A lot of people run into that one.  It's a bug that should be fixed, hopefully in Gutsy.

---

### Post by redsox59 on 2007-07-13
Although now it seems I only have 1 desktop. How do I fix that one?

edit: seems to be working now, not sure how that happened but whatever.

---

### Post by bdtgp on 2007-07-13
If it happens again, go into General Options and change your horizontal virtual size to 4.

---

