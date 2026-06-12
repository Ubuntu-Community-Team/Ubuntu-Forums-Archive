---
title: "Icons in the Gnome shell"
date: 2011-11-24
forum: Desktop Environments
---

### Post by Mazate on 2011-11-24
I installed world of warcraft in wine and I installed another application that I downloaded from a website.  Both have placed launch icons on the desktop.  How do I get rid of them without ruining the option to place the icons in the bar on the left?  In the past when having icons automatically placed on the desktop, if I deleted them it also deleted the icon in the activities menu if I tried to move it to the launcher bar.  I hope I was able to articulate the problem.  Any assistance would be most appreciated.

---

### Post by ShodanjoDM on 2011-11-24
> **Mazate said:**
> I installed world of warcraft in wine and I installed another application that I downloaded from a website.  Both have placed launch icons on the desktop.  How do I get rid of them without ruining the option to place the icons in the bar on the left?  In the past when having icons automatically placed on the desktop, if I deleted them it also deleted the icon in the activities menu if I tried to move it to the launcher bar.  I hope I was able to articulate the problem.  Any assistance would be most appreciated.

How about moving the corresponding *.desktop file to ~/.local/share/applications/ ?

Like this for example - sorry for the name of the file though, never played WoW so I don't know the correct name for it: 

```
mv ~/Desktop/WoW.desktop ~/.local/share/applications/
```

---

