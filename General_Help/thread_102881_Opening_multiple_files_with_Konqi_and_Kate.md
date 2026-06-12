---
title: "Opening multiple files with Konqi and Kate"
date: 2005-12-13
forum: General Help
---

### Post by alvonsius on 2005-12-13
Hey all. I have a problem here.

Last night I updgare to KDE 3.5, and found out that opening multiple files (source files,like PHP, C, etc) by doubleclicking them on Konqueror opens new session of Kate for each files. So when I doubleclick 3 PHP files in a sequence, there will be 3 opened Kate windows on my desktop.

Any hint??? Because back then when I use 3.4.3 the new opened files will open in the same session (window) of Kate. Thanks ...

PS: KDE 3.5 rocks ... I really like the taskbar and windec

---

### Post by daller on 2005-12-13
I don't know, but it might be a problem with kate's .desktop file....

See here:

[http://ubuntuforums.org/showthread.php?t=96227](http://ubuntuforums.org/showthread.php?t=96227) (my post)

---

### Post by GoldBuggie on 2005-12-13
This is a one highly annoying problem which I haven't found a solution to yet. The desktop files might be the solution but what is it that needs changing..hmmm

---

### Post by alvonsius on 2005-12-13
[QUOTE=daller]I don't know, but it might be a problem with kate's .desktop file....

See here:

[http://ubuntuforums.org/showthread.php?t=96227](http://ubuntuforums.org/showthread.php?t=96227) (my post)[/QUOTE]

Like you said, i hack the ~/.local/share/applications/kde-kate.desktop and changed this line

```
Exec=kate %U
```

into

```
Exec=kate --use
```

It solve the problem, the opened files using the same session of kate. But now another problem comes ... It shows an alert "**KDEInit could not launch 'kate'**" eveytime I open a file.

Any hint???

---

