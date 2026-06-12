---
title: "How do I put current Blender in the correct menu category?"
date: 2016-08-22
forum: Desktop Environments
---

### Post by lukon on 2016-08-22
I've got 16.04.

I'm taking an on-line course that requires me to install the most current version of Blender, which of course is not in the Ubuntu repositories, so I've got to go direct, putting Blender in my /home/luke/Blender directory.


Once I do install it, the menu editor refuses to put Blender in the graphics category of applications, instead locking it into the "other" category. This really annoys me. What good is a menu editor that won't let you actually categorize the applications the way that makes sense?

Anyway, does anybody know how I can get the latest Blender installed and properly categorized in my menu (Classic menu indicator)?

---

### Post by &amp;KyT$0P# on 2016-08-22
Edit your Blender .desktop file in a text editor, add a line like this
```
Categories=Graphics;
```

---

### Post by CantankRus on 2016-08-23
You may be interested in installing blender from [**_[COLOR="#B22222"]THIS PPA[/COLOR]_**]("https://launchpad.net/~thomas-schiex/+archive/ubuntu/blender") where it will work as your other applications
and be updated.
It will also appear in the graphics section.

If not just use the **blender.desktop** file that is in your extracted blender folder as a reference when creating your own .desktop launcher.

---

### Post by riazkhan520 on 2016-08-27
[Desktop Entry]
Name=the name you want shown
Comment=
Exec=command to run
Icon=icon name
Terminal=false
Type=Application
StartupNotify=true

---

### Post by lukon on 2016-08-28
Thanks to you all! My motherboard BIOS just broke, so I won't get a chance to try these solutions until I replace that motherboard and rebuild the computer.

---

