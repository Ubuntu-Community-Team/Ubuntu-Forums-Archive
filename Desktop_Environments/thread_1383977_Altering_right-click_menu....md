---
title: "Altering right-click menu..."
date: 2010-01-17
forum: Desktop Environments
---

### Post by Izobalax on 2010-01-17
OK, so I discovered how to change the right-click menu on KDE 4.4 RC1, which is awesome, I configured it to bring up my applications menu on right-click. Whilst this is good, I did forget to change it back. And now I can't bring up the Desktop Activity menu to change wallpaper etc. 

Woops. 

Any hints for me? Hidden config files I can alter?

/izo\

---

### Post by Izobalax on 2010-01-18
Bump.

/izo\

---

### Post by Zorael on 2010-01-18
The (only?) other way to get to that settings dialog is via the desktop cashew. Hit it and pick Desktop Activity Settings.

---

### Post by Izobalax on 2010-01-18
> **Zorael said:**
> The (only?) other way to get to that settings dialog is via the desktop cashew. Hit it and pick Desktop Activity Settings.
Hi, thanks for reply! Unfortunately, I've already been doing that... all it does is minimize all applications... no menu. =(

/izo\

---

### Post by Zorael on 2010-01-18
You mean, clicking the cashew minimizes all windows? It doesn't open up a pop up menu where you can pick Desktop Activity settings? That sounds like a bug you might want to report, if it's consistently reproducible.

Anyway, the manual workaround is to edit **~/.kde/share/config/plasma-desktop-appletsrc** and find the section that begins like this.
```
[Containments][***<number>***][ActionPlugins]
```
***<number>*** is probably **1** if you only have one activity set up. Make it look like this (assuming 1);

```
[Containments][1][ActionPlugins]
**RightButton;NoModifier=contextmenu**
```

---

### Post by Izobalax on 2010-01-18
> **Zorael said:**
> You mean, clicking the cashew minimizes all windows? It doesn't open up a pop up menu where you can pick Desktop Activity settings?


Correct.

> **Zorael said:**
> That sounds like a bug you might want to report, if it's consistently reproducible.


Cool. How do I do that?


> **Zorael said:**
> Anyway, the manual workaround is to edit **~/.kde/share/config/plasma-desktop-appletsrc** and find the section that begins like this.
```
[Containments][***<number>***][ActionPlugins]
```
***<number>*** is probably **1** if you only have one activity set up. Make it look like this (assuming 1);

```
[Containments][1][ActionPlugins]
**RightButton;NoModifier=contextmenu**
```


Excellent. I shall try this and report back. 

/izo\

---

### Post by Izobalax on 2010-01-18
> **Izobalax said:**
> Excellent. I shall try this and report back. 

/izo\


Unfortunately, this didn't work, right-clicking still brings up the applications menu. I was able to change the wallpaper in the file, however, which is nice. Mine reads:

```
[Containments][24][ActionPlugins]
MidButton;NoModifier=contextmenu
RightButton;NoModifier=applauncher
wheel:Vertical;NoModifier=switchdesktop
```

/izo\

---

### Post by Izobalax on 2010-01-18
> **Izobalax said:**
> Unfortunately, this didn't work, right-clicking still brings up the applications menu. I was able to change the wallpaper in the file, however, which is nice. Mine reads:

```
[Containments][24][ActionPlugins]
MidButton;NoModifier=contextmenu
RightButton;NoModifier=applauncher
wheel:Vertical;NoModifier=switchdesktop
```

/izo\

*facepalm* I've just realised what the problem is. My MIDBUTTON is now contextmenu! And I've just tried it and it works! I'm an eejit. Thank you very much!

/izo\

---

### Post by benerivo on 2010-01-18
I think the problem with that kde4 option is you can't bring the config window back up, and it doesn't appear anywhere else, such as in system settings. Holding Alt then pressing (not holding) d then s brings it back up.

---

### Post by Zorael on 2010-01-18
But I *can* bring that config window back up. :<

Doesn't yours behave as in the attached screencast?

---

### Post by Izobalax on 2010-01-18
> **Zorael said:**
> But I *can* bring that config window back up. :<

Doesn't yours behave as in the attached screencast?
Nope. It just lightens up, minimizes the windows.

/izo\

---

### Post by benerivo on 2010-01-18
My cashew also just minimises the window -- there is no menu, it just minimises/restores the current window. I should point out that this pc is running arch linux with the kde4.4 beta release.

---

### Post by benerivo on 2010-01-19
Just to confirm what is happening to my cashew (and possibly also Izobalax's), i have tried moving my panel from the side of the screen to the bottom and the cashew now works fine. When i have my panel on the right hand side, it seems to interfere with the cashew (which is in the top right of the screen) and when i click it, it just 'Shows the Desktop', but does not bring up the cashew menu.

---

