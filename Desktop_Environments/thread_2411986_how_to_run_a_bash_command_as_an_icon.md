---
title: "how to run a bash command as an icon?"
date: 2019-02-06
forum: Desktop Environments
---

### Post by bullethead on 2019-02-06
I've just finished setting up Ubuntu install for my elderly mother.  She plays this flash bubble game, want to know if there is an app that can run commands and make it an icon.

something like "sh gnash /home/user/bubble_shooter.swf"

she's using Ubuntu LTS 18.04

this software has gotten so easy to use over the years I am sure it is a basic request.  Pardon my ignorance, I'm getting pretty old too for this.

Would like to make this an icon on the favorites launcher for her.  Solitaire already works great, she's bugging me for this.  I had it setup on an older machine with Lubuntu but I can't figure this out in Ubuntu.

Thanks

---

### Post by ajgreeny on 2019-02-06
I have never used gnash or anything else to play local swf files so can't comment about that but if the command ```
gnash /home/user/bubble_shooter.swf
``` will play bubble_shooter in gnash you simply need to create a bubble_shooter.desktop file to add to the desktop.  I am also assuming that bubble_shooter.swf is a local file already downloaded onto the disk and not an online network game normally played in a browser like firefox. 

I am also, however, not sure if the gnome desktop folder of Ubuntu will allow launchers on the desktop, and I don't use gnome to test that, but if it does your .desktop file will need to contain something like the following text.
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Bubble Shooter
Comment=Play Bubble Shooter game
Exec=gnash /home/user/bubble_shooter.swf
Icon=path/to/icon/of/your/choice
Categories=GTK;Games;
Terminal=false
StartupNotify=false

```
Give it a try and see if it works for you.

---

### Post by bullethead on 2019-02-06
thank you all very much.  I figured it out.  

I put the "bubble_shooter.swf" in the desktop folder using the file manager.  I set permissions when I right clicked it to be able to execute as a program, and then set the open with tab to use gnash.  Now she can click on that on the desktop and it opens up.

This was easier than I thought, thank you very much for helping it got my mind working.

---

### Post by ajgreeny on 2019-02-07
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

