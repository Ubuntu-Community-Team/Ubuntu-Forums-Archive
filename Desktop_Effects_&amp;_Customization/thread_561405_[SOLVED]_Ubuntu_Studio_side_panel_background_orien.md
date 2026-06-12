---
title: "[SOLVED] Ubuntu Studio side panel background orientation"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by twiggyness2000 on 2007-09-27
I am using ubuntu studio (feisty) and my goal in this thread is to change the background image for the gnome panel.  The catch:  I am using a side panel, which uses the same image orientation as the top/bottom panel does.  I think the actual image is in

```
/usr/share/themes/UbuntuStudio/gtk-2.0/panel
```

Now, in Studio you can't change the panel background image w/o changing the entire theme from UbuntuStudio to something else first.

Desktop example below....

I normally don't set the panel fully expanded, but you see the point I'm trying to make.  I think one or both of the text files in the /usr/share/themes/UbuntuStudio/gtk-2.0/ and the /panel sub-dir have something to do w/it, but I'm not a scripter or programmer.  I've tried to add an additional image into the directory which consists of the default image turned 90 degrees counterclockwise(named it panelright.png) and then went to the panel's properties box and changed the background of the panel....but the *whole* panel doesn't change.   Maybe there's a separate button background i'm not aware of...anyhow, i'm open to suggestions.

---

### Post by twiggyness2000 on 2007-09-30
[Solved]
I wasn't looking for transparency, but this other thread gave me the hint I needed to disable the Studio's calls for the original .png, and then I manually re-applied the separate .png file I made to the side panel as I saw fit.

See this thread for details--and only rem out (comment out) the bold lines.

[http://ubuntuforums.org/showthread.php?p=3233103&highlight=bg_pixmap%5BNORMAL%5D#post3233103]("http://ubuntuforums.org/showthread.php?p=3233103&highlight=bg_pixmap%5BNORMAL%5D#post3233103")

---

