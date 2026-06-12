---
title: "icons stuck on desktop (not in launcher)"
date: 2013-11-25
forum: Desktop Environments
---

### Post by cebowlin on 2013-11-25
I have three icons on the desktop that I cannot remove.

---

### Post by Frogs Hair on 2013-11-26
Can you describe what they are ?  The Gnome Tweak has options for desktop icons and they can be disabled from that tool . (Tweak Tool > Desktop)

---

### Post by cebowlin on 2013-11-26
the three icons are, home, trash, and computer.  I am a real beginner with ubuntu, and will need some basic instructions to succeed

---

### Post by Frogs Hair on 2013-11-26
Those are the icons that can be added or removed from the Tweak Tool . I assume you are using Unity because you wrote launcher if this is not correct please specify your Ubuntu version.

For Unity, type Tweak Tool into dash and open the application . Under the desktop category there is an on/off selector for desktop icons . If the Tweak is not installed it can be found in the software center. I don't remember Ubuntu having icons by default so if you are using Xubuntu or Lubuntu the method will be different.

---

### Post by cebowlin on 2013-11-26
I found the twek tool and was unable to remove the icons from the desktop.  I did reset the defaults in tweek.  Still no luck.

---

### Post by Frogs Hair on 2013-11-26
Try logging out and back in . I have never had to do that , but it my help. I'm wondering how they got there to begin with . Desktop icons appear in XFCE, but I have never seen them in Ubuntu unless they were added using one of the Tweak Tools.

---

### Post by cebowlin on 2013-11-26
I did try logging in and out a few times.  I had never been into tweak before your imput.  I have the duel boot (ubuntu and windows 7}, but I don"t think that matters.  This issue just came up a couple day ago and i have been using the dual boot a month or so.  I really do appreciate your help, thanks much, if you think of anything, let me know

---

### Post by stinkeye on 2013-11-26
Have you installed nemo or another desktop session lately.

Results from these 2 terminal commands...
```
gsettings get org.gnome.desktop.background show-desktop-icons
gsettings get org.nemo.desktop show-desktop-icons
```

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **gsettings get org.gnome.desktop.background show-desktop-icons**
true
[COLOR="#008000"]glen@Raring:~$[/COLOR] **gsettings get org.nemo.desktop show-desktop-icons**
false
```

---

### Post by cebowlin on 2013-12-10
I have home, trash, and computer icons on desktop that I cannot remove.  I'm duel booted with windows 7/ubunta.  any thoughts on how to remove them

---

### Post by coffeecat on 2013-12-10
Threads merged. Please do not start duplicate threads about the same problem. This dilutes community effort.

---

