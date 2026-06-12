---
title: "Anyone else having stability problems with Gnome shell in 12.04?"
date: 2012-05-29
forum: Desktop Environments
---

### Post by Macfunky on 2012-05-29
I am loving 12.04. I'm torn between Unity and Gnome shell but i think i prefer Gnome shell, although i miss features in Unity when i'm not using it. I don't care what anyway says, they both work great for me :) 

Anyway, onto my problem. I have Gnome shell installed and i am mostly using that. Every once in awhile, randomly and perhaps every few days, Gnome shell logs me out with no warning. I haven't had this problem with Unity although i would really prefer if i could stick with Gnome shell. Anyone encounter this problem or is it just me? I have my system up to date. It runs so smoothly normally but obviously it logging me out and me losing my work is not a good thing. Any help?

---

### Post by VanillaMozilla on 2012-05-29
It's possible for the desktop to crash, and that's what's happening.  It's almost certainly a bug.

And yes, this has happened to me with the Gnome 2 desktop.

---

### Post by Frogs Hair on 2012-05-29
You may want to check looking glass for errors to try and figure out what's happening.  Alt + F2 ```
lg
```Esc to Exit

---

### Post by Macfunky on 2012-05-29
> **Frogs Hair said:**
> You may want to check looking glass for errors to try and figure out what's happening.  Alt + F2 ```
lg
```Esc to Exit

I'm assuming i can run that after logging back in and it'll list out processes before and up to when it crashed? I'm not at my computer now but i will try that out next time i'm on it and it happens. Cheers.

---

### Post by markbl on 2012-05-29
See my comment to a similar question here [http://ubuntuforums.org/showthread.php?t=1985976](http://ubuntuforums.org/showthread.php?t=1985976).

---

### Post by Macfunky on 2012-05-30
> **markbl said:**
> See my comment to a similar question here [http://ubuntuforums.org/showthread.php?t=1985976](http://ubuntuforums.org/showthread.php?t=1985976).

Thanks for that. At least I know what's the cause now. That's very frustrating. The previous driver also had issues. Is this the driver or ubuntu's fault and do you know if either are aware of the problem?

---

### Post by markbl on 2012-05-30
Seems to be an nvidia bug introduced since 295.40 and in all versions since (295.49, 295.53, 302.07). It causes an xorg segmentation fault. Various people have provided core dump stack traces around the forums and bug databases since at least the release of Ubuntu 12.04 but there doesn't seem to be any action/comment from nvidia (or even canonical) about it which just astounds me.

---

### Post by traditionalist on 2012-05-30
I had them. Removed unity and had none since, although I also have a flakey graphic driver ( ATI)

---

