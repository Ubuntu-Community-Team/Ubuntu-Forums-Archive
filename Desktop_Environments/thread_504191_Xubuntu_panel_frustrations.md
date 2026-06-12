---
title: "Xubuntu panel frustrations"
date: 2007-07-18
forum: Desktop Environments
---

### Post by e6626550w on 2007-07-18
How do you keep the icons in the top panel to stay where you want them to? Everything was fine and then the ones in the right hand side , the 'shutdown' and whatever else was there, went flashing over to the left hand side and no way in hell could I find how to get them back over to the right side. Click the 'move' and drag them over to where I wanted them and they then would rush right back to where they had started from. 

I played with the xfce settings menu until I was blue in the face and nothing helped there. Is there a known bug concerning this? 

Incidentally, something else weird is that the known bug with the terminal crashing the program and returning you to the login  screen doesn't happen in gnome. The xfce terminal works fine in Gnome but still crashes In the Xfce session unless you modify the .xorg.conf file. ( I loaded the xubuntu desktop on top on ubuntu) 

thanks,
eileen...

---

### Post by ugm6hr on 2007-07-19
The panel issue:

I suspect you have accidentally deleted the "spacer" that separated the left-sided and right-sided icons on the panel.  Or you might have moved the "spacer" to the right side.

To check - right-click on the blank grey part of the panel on the right, and click Properties.  It should say "Separator or spacer" in the settings window.  Make sure the "expand" box is ticked, and close.

Right-click again on spacer, and select Move.  Then move mouse to where you want to separate left and right-sided icons, and left click.

That should work.  If the first step doesn't work - you may have to Add New Item and select Separator or Spacer, then try the instructions again.

The terminal issue:

I don't have any such issue.  I thought it only affected Xubuntu installations from the AlternateCD...  Obviously not.

---

