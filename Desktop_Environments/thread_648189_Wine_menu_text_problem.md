---
title: "Wine menu text problem"
date: 2007-12-23
forum: Desktop Environments
---

### Post by llvllarten on 2007-12-23
I've installed wine few weeks ago.
First it worked without problems. But after installing a dutch dictionary (Van Dale) the text in the Wine configuration menu and all the windows applications changed to a strange font. (see picture in attachment)

I've tried so far:
-searching info on forums
-changing font of wine
-installing different Wine theme (windows luna)
-removing and reinstalling Wine
-removing all installed Windows applications

Nothing works...

Can anyone help me?

---

### Post by markharding557 on 2007-12-30
try deleting /home/user/.wine and rerunning winecfg you will have to reinstall your wine programs afterwards

---

### Post by urukrama on 2007-12-31
I have a similar problem, but with me the font is still readable. I still have to search for a solution (I don't want to deal with it now :p).

[This]("http://ubuntuforums.org/showthread.php?t=103357&highlight=wine+change+fonts") thread is about a similar problem. Perhaps the solution given there works in your (and my) case as well.

EDIT: and perhaps [this]("http://justlinux.com/forum/showthread.php?t=141123") too?

EDIT2: The first post I linked to solved my problem, though it isn't really a solution (you have to delete a font, but what if you actually want to use that font for something else?). I still can't change the fonts with DisplaySet (see [here]("http://ubuntuforums.org/showthread.php?t=142741")), though, as I could before these problems arose.

---

### Post by kest on 2007-12-31
I had a similar problem just a while ago, though my font was still readable, if just barely. I was well into looking for a registry-based solution when I happened to try copying an arial.ttf into the otherwise empty ~/.wine/drive_c/windows/fonts (if memory serves) directory, which seemed to make Arial the default font.

---

### Post by llvllarten on 2007-12-31
Problem solved! 
Deleting the "Van Dahle" ttf file from ~/.wine/drive_c/windows/fonts/ solved the problem for me.
Whiteout reinstalling wine.

thnx guys!

---

