---
title: "No borders on compiz fusion"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by waggygee on 2007-07-11
I had some problems with beryl and compiz and window borders, I ddnt have any window borders. I restored a backup from before installing beryl and installed compiz fusion from scratch but I still have no windows borders! I have tried the "compiz --replace" set of commands that are added to the window you get when you click Alt+F2.... Help! Please!

---

### Post by tgm4883 on 2007-07-11
> **waggygee said:**
> I had some problems with beryl and compiz and window borders, I ddnt have any window borders. I restored a backup from before installing beryl and installed compiz fusion from scratch but I still have no windows borders! I have tried the "compiz --replace" set of commands that are added to the window you get when you click Alt+F2.... Help! Please!

compiz --replace -c emerald

:EDIT:

Well the fix is to run "emerald --replace &".  But I start compiz with the above and it works

---

### Post by bdtgp on 2007-07-11
I would try this.

Add this to your /etc/X11/xorg.conf under the device section of your video card:
```
Option "AddARGBGLXVisuals" "True"
```

Then run this command when you hit Alt+F2:
```
compiz --replace &
```

Make sure you have that "&" sign at the end.  Hope that helps!

---

### Post by waggygee on 2007-07-12
OK cool! I got borders!! But now theres no reflection effect and when I change settings in the CompizConfig Settings Manager there is no effect

---

### Post by bdtgp on 2007-07-12
Sorry but I'm not sure what to tell you there, I am having the same problem.  Does anyone else know the solution?

---

### Post by waggygee on 2007-07-15
oh, and my update manager keeps saying I should update. In the list or "other updates" it has 17 'updates' that are all compiz, compiz-core, compiz-plugins-extra, emerald etc.... these are all already in (except compiz-core I think as it was removed when I put compiz fusion in)

---

### Post by tgm4883 on 2007-07-15
> **waggygee said:**
> oh, and my update manager keeps saying I should update. In the list or "other updates" it has 17 'updates' that are all compiz, compiz-core, compiz-plugins-extra, emerald etc.... these are all already in (except compiz-core I think as it was removed when I put compiz fusion in)

What do you mean already in?  You will get lots of updates with compiz fusion as it is currently under development.

---

### Post by waggygee on 2007-07-16
> **tgm4883 said:**
> What do you mean already in?  You will get lots of updates with compiz fusion as it is currently under development.

What I mean by 'already in' is that these files are in already, as in they were installed at time earlier than now.... they were installed in the past and not removed (I hope that is clear enough). The packages are not updates as the are identical. Its not that its a big issue or anything, I just wanted to know if I was the only one who was experiencing this

---

### Post by bdtgp on 2007-07-16
They may appear identical but there are differences and they are updates.  if for some reason they aren't then it couldnt hurt to install them.  just be prepared to see pretty frequent updates for compiz.

---

### Post by waggygee on 2007-07-16
> **bdtgp said:**
> They may appear identical but there are differences and they are updates.  if for some reason they aren't then it couldnt hurt to install them.  just be prepared to see pretty frequent updates for compiz.

All the numbers and such look identical to me.... Ill run the updater several times and see if it stops

---

