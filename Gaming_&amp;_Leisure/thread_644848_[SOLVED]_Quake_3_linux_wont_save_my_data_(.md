---
title: "[SOLVED] Quake 3 linux wont save my data :("
date: 2007-12-19
forum: Gaming &amp; Leisure
---

### Post by TidusBlade on 2007-12-19
I installed Quake 3 with linux binaries and the patch aswell, and the gameplay is running perfectly, however, It dosent save my settings made in the options and for example, I unlock Tier 2, and then I quit the game and go back in, I have to do Tier 1 again... And at the end of each battle it says something like cannot write or save to q3config.cfg and I chmodded the quake 3 folder to allow it to but to no luck :(
If anyone has any idea what I should do I would appreciate it :)

---

### Post by Perfect Storm on 2007-12-19
How did you install it and where and how do you launch the game? Sounds like you don't have permission to save to the config/save.

---

### Post by TidusBlade on 2007-12-19
Dragged the files off the CD and installed it by using "sudo bash setup.sh" and I run it by going to the dragged files and typing "bash quake3.sh" 
All in terminal.

---

### Post by Perfect Storm on 2007-12-19
Any chance that you hit the play button in the installer window?

---

### Post by TidusBlade on 2007-12-19
The installer was terminal based for me.... 
Only the patch had a GUI and no play button
But the installation asked me if I wanted to play Quake 3 right after the installation and I said yes, if that matters.

---

### Post by zcal on 2007-12-19
Yep, it matters.  If you went straight into playing the game from the installer, then your first play was as root, so all the config files were initially set to accept root permissions, which is why you can't save anything if you DON'T play as root.  Obviously, this is not desireable.

I think the config files should still be in your home directory.  If that's the case, all you have to do is use root permissions to delete your .quake3 folder, then run the game as normal.  It'll generate a new .quake3 folder that won't require root permissions to be saved to.

---

### Post by TidusBlade on 2007-12-20
Oh ok thanks alot! Ill try it out when I get back from my aunt's house.

---

### Post by SoberWarlock on 2007-12-20
Now I know in the future not to launch the game at installation window.

---

### Post by Perfect Storm on 2007-12-20
> **SoberWarlock said:**
> Now I know in the future not to launch the game at installation window.

It goes with all games you want to install globally.

---

