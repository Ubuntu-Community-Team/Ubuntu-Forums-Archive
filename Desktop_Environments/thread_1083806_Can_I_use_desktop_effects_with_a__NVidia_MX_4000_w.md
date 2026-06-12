---
title: "Can I use desktop effects with a  NVidia MX 4000 with restrcted drivers"
date: 2009-03-01
forum: Desktop Environments
---

### Post by Farmer of Bricks on 2009-03-01
I am currently running a up-to-date install of Intrepid x64 with KDE4.2, a NVidia MX 4000 GPU, and a AMD Athlon 64 processor. 
Can I safely click on the box "enable desktop effects" System Settings?
The last time I clicked, without the restricted driver, I had to reinstall intrepid because I coudn't find how to undo the click from without the KDE4.1 GUI. Now, using KDE4.2 and the restricted driver, can I safely check that box?

```

blk@blackbox:~$ fortune
You single-handedly fought your way into this hopeless mess.

```

---

### Post by Monsieur Gonzalez on 2009-03-01
From [KDE's guide to Kde4.2]("http://www.kde.org/announcements/4.2/desktop.php"), "KWin uses 3D effects by default if it detects the computer is capable of running them reasonably. You can take control and disable these checks or change settings (Such as the global animation speed) to fine tune your experience. When your computer is under heavy load, KWin will automatically disable the compositing temporarily to keep things running smoothly, and notify you. You can re-enable compositing by pressing "SHIFT+ALT+F12"

So, seems like it should work.

---

### Post by Farmer of Bricks on 2009-03-01
accidently hit Ctrl+Alt+F1, which kicked me out to a terminal.
Now I know the command ```
reboot
```
Shift+Alt+F12, you say? I can't see any difference before or after I hit Shift+Alt+F12, but I haven't checked the box in Systemsettings yet.

---

### Post by Monsieur Gonzalez on 2009-03-01
From the article, it looks like desktop effects should be auto-enabled if kde detects your card supports them. From what I remember, when you enable the effects you get a confirmation timer, and the settings revert to default if you don't confirm the choice.

Ctrl+Alt+F1 takes you to a terminal, and Ctrl+Alt+F7 takes you back to the X server, no need to reboot.

---

### Post by Farmer of Bricks on 2009-03-02
How long does the timer last? This helps in figuring if I'v borked my install, which I haven't yet. Yet.

---

### Post by Monsieur Gonzalez on 2009-03-02
When I enable "Enable desktop effects" there's a 10 seconds timer before reverting the option.

---

