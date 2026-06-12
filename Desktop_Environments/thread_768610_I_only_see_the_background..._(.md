---
title: "I only see the background... :("
date: 2008-04-26
forum: Desktop Environments
---

### Post by BlackIrish on 2008-04-26
Hi.

I've just installed Ubuntu 8.04, and after installing the nvidia-new drivers, and trying to enable the special effects in the "appearence" tool, I've restarted my computer.

Now when I load ubuntu, all I see is the background. Note that everything is working cool, like I can make folders, drag the selector, I even opened firefox (this was after I opened the help center, and clicked on "make a translation" so  I can get to firefox :D ), but I don't see the top and bottom toolbars.

Any fixes? I guess I have to remove the nvidia drivers or some a toolbox mentioned some "restricted drivers" were in use...

---

### Post by Linja on 2008-04-26
You shoul be able to re-add those bars (they are called panels) by right-clicking on your screen and selecting "add panel".

---

### Post by BlackIrish on 2008-04-26
No such option dude, I can make folders, documents, launchers, allign and change background image but not add panels...

---

### Post by Linja on 2008-04-26
Try running gnome-panel from the command line (see below in case you can't launch a terminal).
If that doesn't work, use both of these commands:
sudo aptitude remove gnome-panel
sudo aptitude install gnome-panel
If you can't launch a terminal, hit ctrl+alt+F1, do your work, then return to your GUI with alt + F7.
Bear in mind that removing gnome-panel is going to remove alacarte and gnome-applets as well. You may need to sudo aptitude install those individually if they don't get reinstalled along with gnome-panel.

---

### Post by BlackIrish on 2008-04-26
Wow!

There wasn't any need to remove gnome-panel, since it wasn't even there in the first place.

I just installed it now, logged out and logged it, and it works great!

Just it had some error about some file about fast user switching, so I just clicked delete file... errrr guess no fast user switching for me anymore :p

Anyway, thanks dude!

---

### Post by isomorph on 2008-04-28
I tried the sudo remove ... and install... again.

No changes at al. The panels are still not here.


cheers

Iso

---

### Post by newbie2 on 2008-04-29
> **Linja said:**
> Try running gnome-panel from the command line (see below in case you can't launch a terminal).
If that doesn't work, use both of these commands:
sudo aptitude remove gnome-panel
sudo aptitude install gnome-panel
If you can't launch a terminal, hit ctrl+alt+F1, do your work, then return to your GUI with alt + F7.
Bear in mind that removing gnome-panel is going to remove alacarte and gnome-applets as well. You may need to sudo aptitude install those individually if they don't get reinstalled along with gnome-panel.
had the same issue....sudo aptitude install gnome-panel helped for me...tnx;)

---

