---
title: "custom menu icon"
date: 2010-12-27
forum: Desktop Environments
---

### Post by MichaelBurns on 2010-12-27
I have successfully added a new menu item:
Applications > Games > Galaga
using a $HOME/.local/share/applications/Galaga.desktop file containing:
```

[Desktop Entry]
Type=Application
Version=1.0
Name=Galaga
GenericName=a single-screen space shooter
Comment=Enjoy your Galaga, Mom!
Icon=$HOME/.fceultra/icons/galaga.png
TryExec=fceu
Exec=fceu $HOME/.fceultra/roms/galaga.nes
Categories=Game;

```
The game runs by clicking the menu entry, as expected, but the cool little icon that I downloaded for it doesn't work.  It is a 48x48 png file.  I can see it as a thumbnail for itself in Thunar, and also in Image Viewer, but next to the name in the menu, where there should be the icon, it is just blank.

How do I get the icon to appear?

BTW, for anyone else trying to add a game to their Games menu, pay attention: the Categories value is Game, not Games!  I figured this out finally by just looking at example .desktop files in the /usr/share/applications/ directory; I useful tip in general.

---

### Post by mrkazoodle on 2010-12-27
Have you tried using alacarte?

edit:
I just added a new menu entry using alacarte and chose a png file as icon, so it clearly isn't because png wouldn't be supported or something like that.

---

### Post by MichaelBurns on 2010-12-27
> **mrkazoodle said:**
> Have you tried using alacarte?I don't understand your question, so probably not.

---

### Post by hhh on 2010-12-28
mrkazoodle, alacarte is a gnome menu editor, MB the OP is using Xubuntu.

Try using the full path to your icon, i.e. Icon=/home/USER_NAME/.fceultra/icons/galaga.png

replace USER_NAME with... well, you know.

---

### Post by MichaelBurns on 2010-12-28
> **hhh said:**
> Try using the full path to your icon, i.e. Icon=/home/USER_NAME/.fceultra/icons/galaga.pngWell, that "worked".  Thank you, hhh.  This is a poor solution, though.  I mean, this is a great example of the utility of environment variables.  I can test this out in my non-sudo account, then log into my sudoer, copy over the files, change permissions and ownership, and voila!  It is an extra silly step to have to go in and edit a file, or what if I have 100 user accounts that I want to do this for, then I have to edit 100 files for each game that I set up (not to mention that the process of editting can induce unintentional changes that break the setup).  I should leave some feedback on freedesktop.org suggesting that they should support pathname expansion in all of their keys, not just Exec.  (Did you notice?  $HOME was successfully expanded in the Exec key.)  I will leave this as unsolved for a while in case someone knows how to set pathname expansion in the Icon key.  Thanks again, though.

---

### Post by mrkazoodle on 2010-12-29
I apologize, glad you found a solution to your problem anyway.

---

### Post by MichaelBurns on 2010-12-30
@mrkazoodle:
Thank you for offering a solution anyway.

@hhh:
I just read this thread again, and I must appologize to you.  My previous post seems extremely rude to you, but that was not my intention at all (I must be having bad luck with this lately).  The "poor solution" and "silly" comments were not directed at your suggestion, but rather my pathetic commentary on the way the .desktop file is implemented.  In retrospect, I should have just bitten my tongue, and I suppose that will be a good policy for the future.  Again, I appologize, and thank you for the solution that I *will* probably wind up using.

---

