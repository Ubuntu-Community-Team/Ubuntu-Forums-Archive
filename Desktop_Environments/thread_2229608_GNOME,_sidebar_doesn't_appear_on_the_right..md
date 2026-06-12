---
title: "GNOME, sidebar doesn't appear on the right."
date: 2014-06-14
forum: Desktop Environments
---

### Post by QNEPFmr on 2014-06-14
Hi all, 

I had Xubuntu 13.10 installed and changed the DE to Gnome, after this I've removed all the Xfce stuff, and upgraded to 14.04.
I know that a fresh install is the best thing to do, but I have so many games installed through PlayonLinux that I would give it a shot and see whether my system would break or not.

Everything is working fine for 2 months now besides the fact that the appearing sidebar on the right doesn't appear at all...

Therefore it is impossible to get to the desktop without shutting down Firefox or any other running program.
I have to grab the top en drag it down to get to the desktop.

Does anyone have an idea how I can solve this?

Thx.

---

### Post by Frogs Hair on 2014-06-14
Copy, paste, and run the following command so we know what gnome session is in use . ```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by QNEPFmr on 2014-06-14
Wait, I've fired up gnome-tweak-tool, walked through it, didn't change anything and there he is...??? 
Strange...

(BTW, do you know anything about PlayonLinux and gnome? Does compiz interfere with some of the games? Totally different question, I know...maybe worth opening another topic)

echo $xdg-current-desktop doesn't show anything.

---

### Post by Frogs Hair on 2014-06-14
Strange you should see an output. 

```
echo $XDG_CURRENT_DESKTOP
Unity

```

When logged into the Gnome Shell.

```
echo $XDG_CURRENT_DESKTOP
GNOME
```

---

### Post by QNEPFmr on 2014-06-14
I have tried it again, but no, nothing at all.

Neither on my Arch-based distro, but, when I type echo $DESKTOP_SESSION, it says xfce.
I will give that one a shot on my Gnome machine, later, it's occupied now by the boss. ;)

---

### Post by QNEPFmr on 2014-06-15
:oops:

I should have done it with capitals...

echo $XDG_CURRENT_DESKTOP, says GNOME.

---

### Post by Frogs Hair on 2014-06-15
The favorites dock should appear on the left though in the classic session it won't appear when selecting activities , but will appear when moving cursor to the top left corner.  

Be sure if you are not using the default theme that the theme in use is compatible with the version of gnome in use. You may also want to try restarting the shell also . Alt + F2 ```
r
```

---

### Post by QNEPFmr on 2014-06-15
The favourites dock is on left side all right, what I meant was the multiple desktops bar (1-4) on the right side, that I have seen on my desktop.
But it seems to work now, dunno why it suddenly did though...

Thx!

---

