---
title: "Making desktop shortcut for wine installed game"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by yosser on 2007-06-02
I followed the walkthrough and directions for installing Diablo 2 + exp using wine.

Everything works beautifully, but the wine process did not create a shortcut/launcher on my desktop.

Instead, I have to drop to terminal and winefile then search manually for the executive. Not that much of a pain, but it'd be nice if I could cut out extra steps.

I'm new to ubuntu and non-win OS in general, only a week of using this.

How do I create a desktop shortcut? Thanks!

---

### Post by Alex Fernandez on 2007-06-02
wine "C:/Program Files/...." etc via right click -> create launcher

---

### Post by yosser on 2007-06-02
> **Alex Fernandez said:**
> wine "C:/Program Files/...." etc via right click -> create launcher

When I try doing that, the game doesn't recognize that I have the cd in the drive.

WHen I load the executive through winefile, it works perfect.

What am I doing wrong?

---

### Post by Nehvrook on 2007-06-02
Do you have two CD drives? Some of my wine launchers claim the disk isn't in even though it is. Swapping it to the other CD drive made it recognise the disk. Dunno if it'll help but that's my experience.

---

### Post by yosser on 2007-06-02
> **Nehvrook said:**
> Do you have two CD drives? Some of my wine launchers claim the disk isn't in even though it is. Swapping it to the other CD drive made it recognise the disk. Dunno if it'll help but that's my experience.

actually, what I found out is that I had for some reason hidden the app/wine folder off of the upper panel.

i was able to just right click on the program and have a launcher sent to the desktop.
```

env WINEPREFIX="/home/romel/.wine" wine "C:\Program Files\Diablo II\Diablo II.exe"
```

---

