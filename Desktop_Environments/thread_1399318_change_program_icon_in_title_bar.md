---
title: "change program icon in title bar"
date: 2010-02-05
forum: Desktop Environments
---

### Post by Post Monkeh on 2010-02-05
as the title says, how do i change the default icon used in the title bar (using metacity window manager although i'm running compiz)

i've replaced the swiftfox (and firefox) icons in the usr/share/pixmaps, and usr/lib/<program folder>/icons folders but the icons in the titlebar are staying the same.  what am i missing?

---

### Post by Post Monkeh on 2010-02-06
anyone?

---

### Post by Exp HP on 2010-02-06
I doubt you will have much luck with this.  Applications set their own title bar icons (using ico-format images found in various places in the exe files themselves).  You will need to change the application itself to change the icon.

Or at least, that's the way it is in Windows.  I'm just assuming it's the same way in Ubuntu.  *Maybe* Ubuntu can override icons used in titlebars... but I honestly doubt it.

Many icon editors can find the icon files included in exe files and edit them, but I'm not sure if any have the ability to save them *back* to the exe file.  If I have any luck finding an icon editor that can edit icons and save them back to the exe file without corrupting it, I'll share it.

---

### Post by Post Monkeh on 2010-02-06
didn't realise the icons were hard coded. thanks for the info.

---

### Post by eamon63 on 2010-02-06
you can change the icons you want by replacing particular icons inside icon theme you are currently running. check out the icons inside several 'app' sub-folders in each of these locations:

- /home/<username>/.icons/<your_icon_theme>/
- /usr/share/icons/

---

### Post by wojox on 2010-02-06
> **eamon63 said:**
> you can change the icons you want by replacing particular icons inside icon theme you are currently running. check out the icons inside several 'app' sub-folders in each of these locations:

- /home/<username>/.icons/<your_icon_theme>/
- /usr/share/icons/

The OP is talking about the icon on the top of the application window. Which is really hard to do.

---

### Post by eamon63 on 2010-02-07
unless i completely misunderstood OP, i assumed he meant icons in window title bars. most ubuntu applications have icons in /apps folder (obviously).  try several icon themes, like mac4lin for instance...

---

### Post by Post Monkeh on 2010-02-07
> **eamon63 said:**
> unless i completely misunderstood OP, i assumed he meant icons in window title bars. most ubuntu applications have icons in /apps folder (obviously).  try several icon themes, like mac4lin for instance...

yeah, the icon to the left of the main window titlebar for each application.
it never changes no matter what icon theme is chosen

---

### Post by NormanFLinux on 2010-02-07
I think it does change but there is a bug in Karmic that prevents the title bar from respawning with a new icon.

---

