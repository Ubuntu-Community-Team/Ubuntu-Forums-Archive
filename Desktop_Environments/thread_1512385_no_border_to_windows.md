---
title: "no border to windows"
date: 2010-06-18
forum: Desktop Environments
---

### Post by frriction on 2010-06-18
when I boot to ubuntu I can not see border to windows.

to get it I have to execute the command
```
compiz --replace &

```

then border comes back in terminal there is message
```
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

Is there any work around to not type  compiz --replace & command every time I boot my machine.

---

### Post by stinkeye on 2010-06-18
You could try fusion-icon loaded at startup in startup preferences.

On karmic I used to use ```
fusion-icon -n
```as the startup command.
The -n flag tells it not to load a window manager because it should boot into the window manager you were last using anyway.

Using just fusion-icon as the startup command might solve your problem.
Even if it doesn't, you will have a right click menu in the notification area to reload the window manager.



Also look at your window decorations plugin in CCSM and check the command box says..```
gtk-window-decorator --replace
```

---

### Post by TeoBigusGeekus on 2010-06-18
It seems that the compiz cube is broken cause it can't find the above mentioned picture.
Choose a picture of your liking, save it as ubuntu.png with gimp and put it in the proposed folder.

---

### Post by stinkeye on 2010-06-18
Yes, as TeoBigusGeekus said you are missing that file which I think is a bug in Lucid because I don't think it's included in the Lucid install.
It just refers to a png for cube caps.
CCSM > DESKTOP > DESKTOP CUBE > APPEARANCE
You can just change the link to your own picture.

---

### Post by wojox on 2010-06-18
Also try System > Preferences > CompizConfig Settings Manager and find the "Window Decorations" plugin. Check the box and you're all set.

---

### Post by frriction on 2010-06-18
well i really messed up something really bad to fix this issue and at the end i ended to reinstall ubuntu

Thank you fox for ur suggestions and help.

---

