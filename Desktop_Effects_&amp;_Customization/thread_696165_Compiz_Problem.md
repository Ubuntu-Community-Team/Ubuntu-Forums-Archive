---
title: "Compiz Problem"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by GSZX1337 on 2008-02-13
I have WinXP and Ubuntu on my main HD. I stay in Ubuntu 6 days of the week, and on Saturday I update my site with a new comic. (which I make with Fireworks) Well, eventually I installed Compiz and enabled my choice of effects. Well, I booted into WinXp on Saturday and all went well. On Sunday, I went into Ubuntu and it went into low graphics mode. After fixing it, I restarted my computer and lost all of my effects. 

I un-installed and re-installed Compiz, no dice. I followed the instructions posted in this [thread]("http://ubuntuforums.org/showthread.php?t=529342"). The problem I get now is that I lose my Window bars.

---

### Post by raafaell on 2008-02-13
So, when you started Ubuntu up again after you choose low graphics mode, it did't show Compiz anymore? did you try to set Compiz to boot automatically?

---

### Post by GSZX1337 on 2008-02-13
> **raafaell said:**
> So, when you started Ubuntu up again after you choose low graphics mode, it did't show Compiz anymore?
No, for some reason Ubuntu went into low graphics mode. I turned it back to normal and that's when my Compiz problems stared.

>  did you try to set Compiz to boot automatically?

How can I do that?

---

### Post by sowelie on 2008-02-13
You can add it by going to session options in system -> prefrerences -> sessions.

You're saying your window borders are disappearing when you turn on compiz? Try running the following command in the console:

```
emerald
```

If you get a command doesn't exist error, try installing emerald and see if that helps at all.

```
sudo aptitude install emerald
```

---

### Post by raafaell on 2008-02-13
> **GSZX1337 said:**
> No, for some reason Ubuntu went into low graphics mode. I turned it back to normal and that's when my Compiz problems stared.



How can I do that?

in your MENU, click on System, then Preferences, and then Sessions, when it's open, press on ADD button, and write [COLOR="Red"]compiz[/COLOR], then press OK, and try to restart your system.
Good luck.

---

### Post by mrmiserable on 2008-02-13
most likely your /etc/X11/xorg.conf file has changed to default so open /etc/X11 folder and see if there is backup of your old xorg that worked before and 
find the changes or save as xorg.conf overwriting the new

---

### Post by GSZX1337 on 2008-02-13
> **sowelie said:**
> You can add it by going to session options in system -> prefrerences -> sessions.

You're saying your window borders are disappearing when you turn on compiz? Try running the following command in the console:

```
emerald
```

If you get a command doesn't exist error, try installing emerald and see if that helps at all.

```
sudo aptitude install emerald
```
Thank you. emerald has solved my problem. Now, the only thing is, I have to have a terminal open with emerald. If I close it, window bars go bye bye. Will putting that in my startup Programs fix my new problem? I don't mind having a terminal open since it doesn't really get in the way, it's just that I don't want to accidentally delete it and get rid of my window bars.

---

### Post by GSZX1337 on 2008-02-15
It worked. I didn't have to put emerald in my sessions, though. Thank you all for helping me with my problem.

---

