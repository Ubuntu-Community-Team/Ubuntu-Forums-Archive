---
title: "Gnome-Xfce conflict"
date: 2006-02-14
forum: Desktop Environments
---

### Post by Lanrond on 2006-02-14
After having played around with Gnome for some time, I decided to try Xfce, so I installed xubuntu-desktop.

I have gladly noted a great speed bump, but I would like to continue to experiment with both Desktop Environments.

I logged on and off several times using different session definitions and from some moment on I noticed that Xfce behaves somehow strange. Specifically it had no more custom desktop background, I could not invoke application menu right-clicking with the mouse, and so on.

Anyway Gnome continues to work perfectly well.

I suspect some conflict between the two environments. I browsed the forums searching for hints, but without success.

Has anyone of you any impression to share about this issue?

Thank you.

---

### Post by taurus on 2006-02-14
Do you happen to have nautilus running while you log into Xfce4?  If not sure, this command will show you all the processes currently running!

ps -A

---

### Post by alfonz on 2006-02-14
Yeah, Nautilus (gnome file manager) tends to take over the xfce desktop if not launched by:

```
nautilus --no-desktop
```


if nautilus is running:

```
sudo xfdesktop4
```

I believe that should work. you might have to kill nautilus prior to - sudo killall nautilus

---

### Post by taurus on 2006-02-14
Yes, you have to kill nautilus first before you start xfdesktop4 again...

---

### Post by Lanrond on 2006-02-14
[QUOTE=taurus]Do you happen to have nautilus running while you log into Xfce4?  If not sure, this command will show you all the processes currently running!

ps -A[/QUOTE]

No luck! Nautilus is not running.

Anyway I always log out from my Gnome session before logging in the xfce session, so it seems to me a strange thing if Nautilus would still be running.

Am I wrong?

---

### Post by kaamos on 2006-02-14
the command above should be "xfdesktop" and not "xfdesktop4". That should bring the menu and background back.

EDIT: and what is that sudo doing there? :D

ok, open a terminal and type
```
killall nautilus && xfdesktop
```
and it should work.

---

### Post by Lanrond on 2006-02-14
Waitaminute... are you saying I can safely switch to xfce **without** logging out just by typing those commands in a *puny* terminal? :-)

---

### Post by alfonz on 2006-02-14
> **Lanrond]Waitaminute... are you saying I can safely switch to xfce **without** logging out just by typing those commands in a *puny* terminal? :-)[/QUOTE]

yes you can run the xfce panel in gnome instead of the gnome panel  said:**
> the command above should be "xfdesktop" and not "xfdesktop4". That should bring the menu and background back.

EDIT: and what is that sudo doing there?

ok, open a terminal and type
Code:

killall nautilus && xfdesktop

and it should work.


errrr you got me :-k lol well hey I try not an expert you know, but I do stand corrected

---

### Post by Lanrond on 2006-02-15
Ok, I gathered all the informations and made some tests, but still the same problems remain (no appl menu and no desktop backround). Maybe I messed up with some configuration I haven't figured out yet.

I also tried to launch xfce with sudo and magically the background image reappeared, but next time I could not log in (due to a *.ICEauthority* file permission issue). When I fixed that, the situation reverted to original, previous problems included.

Still testing.

---

### Post by frost242 on 2006-02-15
I experienced the same problem. Saving session didn't help.. I solved this by clearing the cache directory :

```
rm  -rf ~/.cache
```

I hope it helps..

---

### Post by Lanrond on 2006-02-17
Situation update.

I tried all the hints in this thread but to no avail. :-(

Something strange happened last night after I updated (via Synaptic) the new kernel version for Breezy. Rebooting tha Mac, the start screen (the one before the login screen in which you can see the various system services starting) has now the blue xubuntu logo instead of the brown ubuntu one. Then the usual brown Ubuntu login appears and everything goes one as usual.

I assume that having installed xubuntu-desktop changed some setting; is there a way to customize that logo?

EDIT: Never mind I just found out this [HOWTO]("http://ubuntuforums.org/showthread.php?p=631778#poststop")

---

### Post by Lanrond on 2006-02-17
**Solved!** :-)

I finally find out that, probably due to some misbehaviour of mine, I had *erased* xfdesktop from my session configuration. After having launched it and having saved the configuration at log-out, everything reverted to normal.

Thank you all for your help. :)

---

### Post by unit1.cpp on 2007-12-02
I'm getting this same problem. When i logging in xfce session theres only blue xfce wallpaper and theres not any icons, panels. Please help me!

---

