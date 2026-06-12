---
title: "no title bar for Kontact"
date: 2009-02-10
forum: Desktop Environments
---

### Post by aeltester on 2009-02-10
Hey all,
I've got mint 6 (based on ubuntu) on my machine.

I'm former KDE-user so I wanna take all my nice KDE tools (amarok, digikam, kontact) with me. All these used to work fine. Today (I don't think I changed anything lately) I fired up kontact. The weird thing, I've got no window decorations, no title bar and no frame around the window. Moreover, it runs on fullscreen (can't see taskbar and such).
Since I'm working with compiz enabled I'm able to press alt+mouseR and choose Minimize/Maximize/Unmaximize/resize/move... resize doesn't work, neither does alt+mouseM. Only difference between maximized and unmaximized is that in unmaximized state, the window doesn't snap to all the screen-edges immideately when I move it in expo.

I already reinstalled kontact. Doesn't help.

Does anyone know of a config file that might have gotten messed up?

thanks in advance

:P

---

### Post by aeltester on 2009-02-11
solved... just redid the kontactrc in ~/.kde/share/config.

---

### Post by cydejsn on 2009-03-27
Could you be so kind as to tell me what you changed?  I have the same problem. Thanks.

---

### Post by aBitLater on 2009-03-29
same here... if you could, please provide the details to the fix

---

### Post by aBitLater on 2009-03-29
well, here's what I did:

In the kontactrc file, there is this section...

```
[MainWindow]
Height 900=812
State=AAAA/wAAAAD9AAAAAAAABjMAAALMAAAABAAAAAQAAAAIAAAACPwAAAABAAAAAgAAAAIAAAAWAG0AYQBpAG4AVABvAG8AbABCAGEAcgEAAAAAAAAGMwAAAAAAAAAAAAAAIABuAGEAdgBpAGcAYQB0AG8AcgBUAG8AbwBsAEIAYQByAAAAAAD/////AAAAAAAAAAA=
Width 1600=1587
```


Somehow my height had changed to 901, and width had changed to 1601, more than my resolution.  I suspect it has something to do with compiz, which I enabled today.

So, manually change the height and width to something like "100" less than your resolution, then load kontact.  After starting kontact, you can resize it to your choice, and the kontactrc file will be updated automatically.

---

### Post by cydejsn on 2009-03-30
Actually, I found another fix somewhere else. (Sorry, I went to so many different places I cannot give credit where due).  It was a Compiz issue for me as well.  What worked for *me* was to UNCHECK Legacy Fullscreen Support under Workarounds in the CompizConfig Settings Manager.  Just wanted to post this in case it helps anyone else.  Thanks for your reply, aBitLater!

---

