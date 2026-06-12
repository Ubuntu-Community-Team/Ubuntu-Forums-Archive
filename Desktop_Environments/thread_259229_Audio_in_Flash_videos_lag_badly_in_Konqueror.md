---
title: "Audio in Flash videos lag badly in Konqueror"
date: 2006-09-17
forum: Desktop Environments
---

### Post by greggh on 2006-09-17
I decided to install kubuntu-desktop and try it out. I played a few Flash vids in Konqueror and the audio was way out of sync. I immediately open those same vids in firefox and the audio sync is fine. Anyone know what can be causing this in konqueror?

---

### Post by darkvad0r on 2006-09-17
Maybe it's not using the same plugin as firefox (however, afaik, there is no flash plugin for linux that doesn't go out of synch so I'm surprised you don't have the same problem with FF)

---

### Post by greggh on 2006-09-17
I just did another little test in Konqueror while in the Ubuntu desktop and the video and audio are synced. But if I log out and log into the Kubuntu desktop and play a vid in Konqueror then its very out of sync. So I guess it has something to do with the different libraries that are loaded with Gnome and KDE. In Ubuntu/Gnome flash audio synced in both FF and Konqueror. In Kubuntu/KDE flash audio is very out of sync in konqueror but in sync in FF.

---

### Post by manzuk on 2006-10-14
I'm using Kubuntu and in Konqueror, Flash animations in general doesn't have sound. The way to fix it is using the option "enable artsdsp to bypass plugin sounds to arts daemon" (located on the "plugin" tab of Konqueror configuration dialog).
With that enabled, Flash animations have sound, even Youtube videos, but in this case, is out of sync (and not a second; round three or four).

The same happend to me with Firefox a time ago. Flash sound worked really really bad, or not at all. Browsing the forums I found a HowTo that said to use aoss to launch the Flash plugin. How? Changing something in Firefox hidden configuration (the one you have to acces writing something on the address bar, don't remember what). I did it, and since Firefox works ok with flash sound.

So, I just came up with a new solution: if you disable the "... bypass plugin sounds... " option, and launch konqueror like
```
aoss konqueror
```
the sound problem is gone! Don't ask me why. Please, some expert that uses this info to create a final fix to this KDE-Flash sound problem ](*,)

---

