---
title: "Xlib problem"
date: 2006-12-30
forum: Desktop Environments
---

### Post by Didius on 2006-12-30
Hi
I have installed Ubuntu 6.10 on my mother's pc. I would like to amaze her with the desktop graphics.
But I can't seem to get beryl/AiGLX to work, could somebody help?

I would like to run this on a Athlon 1,3 Ghz, with a nVidia TNT2 64MG graphical card.
after I installed edgy i used the "Envy" script ([here]("http://ubuntuforums.org/showthread.php?t=281823")).
nVidea was set up.

Then I followed the [Beryl Wiki guide]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX")
But when i ran glxinfo then, i got this
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
...
```

I searched and if I change the following to "Disable" glxinfo looks good again.
```
Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

What could be the problem?

(sorry for the english...)

---

