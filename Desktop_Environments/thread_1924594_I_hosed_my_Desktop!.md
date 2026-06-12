---
title: "I hosed my Desktop!"
date: 2012-02-13
forum: Desktop Environments
---

### Post by llanitedave on 2012-02-13
At least I still have KDE.  I was in an Xfce session, and tried to get fancy with Compiz and do a little experimentation.  In the Compiz Config Settings Manager, I tried to activate the Desktop Cube and Rotate Cube features.  I got dialog boxes that informed me I'd have to disable the Desktop Wall and Unity plugins, which I foolishly did.

The next time I attempted to log into Unity, I got no dock, no task bar, and no way to select applications, or even log out.  The background services are working, and the desktop wallpaper with its icons are there, and a generic folder menu bar exists, but that's it.

And Xubuntu is hosed too -- same thing.  No multiple desktops, no dock, no application menu.  I can get a little farther by right clicking on the desktop, but I am unable to get the desktop utility to restore my multiple desktops.  All the apps I had on different desktops are just crowded together.

I can get basic functionality in Classic Gnome, and Lxde and KDE both seem to work more or less normally.  Through them, I tried several times to restore Compiz Config Settings Manager to its original settings, including choosing to revert to defaults, but none of that is making any difference.

Is there any kind of configuration file I can use to determine what the correct Unity settings are, and to return them to their proper values?  I'd hate to have to reinstall the whole thing.

Thanks in advance to anyone who can help!

---

### Post by Krytarik on 2012-02-13
Please have look at this guide, with special focus on the "Reset Compiz" part, for resetting Compiz also in regard to XFCE:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by llanitedave on 2012-02-13
I'm flabbergasted sometimes at how you folks manage to come up with the deepest resources for ignorant pikers like me.

Thank you very much, Krytarik!  I went through the instructions on the page, and still nothing was working until I got close to the bottom, and used the following commands from the KDE terminal.
[b]
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
[/b]

That did it!  Unity is now working normally again.  And I'm staying very far away from that Compiz Config Settings tool!

eta:  Although Xfce is still messed up, but I'll be working on that one at a later time.

---

### Post by wildmanne39 on 2012-02-13
Hi, to set up compiz in unity you can use the guide in the sticky at the top of this forum, and please read the guide carefully.
Thanks

---

### Post by pandanuma on 2012-02-14
Krytarik, your link to 'things to do after installing 11.10' was very helpful.  installed gnome-tweak-tools and all my icons came back.
now if I could just get some drivers for my hp monitor I would be happy.
thank you.

---

### Post by Krytarik on 2012-02-14
> **pandanuma said:**
> Krytarik, your link to 'things to do after installing 11.10' was very helpful.  installed gnome-tweak-tools and all my icons came back.
I'm glad that I could help you on the drive-by. :P

---

### Post by llanitedave on 2012-02-15
I used it too, and now, finally, Unity is about 90% of what I want in a desktop.  I've got the rotating cube working almost perfectly, I've shrunk the dock icons so that they're less intrusive and not spilling off the page so much, and I've got decent window decorations and themes going.

Your guidance is well written, and much appreciated, Krytarik.

---

### Post by Krytarik on 2012-02-15
> **llanitedave said:**
> Your guidance is well written, and much appreciated, Krytarik.
Thanks! :D (I'll forward that to my blog partner and actual author of that guide, Sikander; I only edited it.)

---

