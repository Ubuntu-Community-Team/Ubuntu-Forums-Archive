---
title: "[SOLVED] Problem concerning Gnome in Ubuntu"
date: 2007-10-27
forum: Desktop Environments
---

### Post by PmDematagoda on 2007-10-27
I have a big problem concerning Gnome on my Ubuntu 7.10 installation which started occurring after I ran into a problem with Warcraft 3 on Wine after which the entire resolution was off, I managed to fix it by logging of and coming back again but it caused a second, more irritating problem.

The problem is that it takes a very long time to start any applications in the GUI, but it takes only a matter of seconds to start the OS. It also takes a lot of time to get into the GUI itself. I'm willing to do anything to get it back to it's working condition, either reinstalling it or resetting it's configuration files.

I would greatly appreciate any help concerning this matter.

---

### Post by blueturtl on 2007-10-27
Do you have multiple users on the same system? If so, does it take a long time for them to log in and use Gnome as well? If other users don't experience the same slowness, your session file may be corrupt. You can find and delete your session file (while not logged in Gnome of course) in the .gnome2 directory.

---

### Post by PmDematagoda on 2007-10-27
No, I don't have multiple users, but I will give the session file solution a try and tell you how it went.

---

### Post by PmDematagoda on 2007-10-27
No, deleting the sessions file did not work:(. Do you have any other solutions?

---

### Post by blueturtl on 2007-10-27
Well since adding and removing users is so easy, you could just try to add a user for testing purposes, log in as that user and see if the new user also suffers the same problem. If the new user *does not* then the problem is probably limited to your profile settings (ie. the settings files in your home folder). If both users suffer from the same problem, then we have to look at the problem as a system wide problem.

---

### Post by PmDematagoda on 2007-10-27
I did what you suggested and it seems the problem is indeed system-wide. I am thinking of uninstalling Gnome completely and reinstalling it again, how do I do this? I tried:-

```
sudo aptitude purge ubuntu-desktop
```

but it did not yield any results.

---

### Post by blueturtl on 2007-10-27
Reinstalling Gnome may be a bit of a blindshot. I mean you say this started after you ran WarCraft III in WINE and it crashed. That is not supposed to have system wide effects, remember all the things you use are run with user rights, so this could not / should not have modified anything outside your home folder.

Are there any other clues or possible modifications to your system physically or softwarewise right before this problem started? Does the problem survive reboots?

> sudo aptitude purge ubuntu-desktop

This would not work because ubuntu-desktop is a dummy package. It is merely there to ensure that all the applications associated with Ubuntu are installed (aka when you install this package, it installs Gnome, Evolution, OO, etc)... Removing it does nothing. If you really want to go ahead with removing Gnome you should probably search for the gnome core-packages in synaptic. When you select them for removal Synaptic will automatically inform you of other packages that need to be removed because they depend on a spesific package. To restore everything all you need to do is 'sudo apt-get install ubuntu-desktop'.

To test your hardware you could try running the Ubuntu Live CD. It is slow, so it may not be perfect for testing system sluggishness, but it may give you an idea.

Something interesting to consider also: running games with 3D graphics is a pretty intense task for the system, is it possible WarCraft crashed because of overheating? If you're running an Intel system, it can in some cases decrease your CPU speed to compensate for inneficient cooling.

---

### Post by PmDematagoda on 2007-10-27
I know it is not something with my PC because Warcraft 3 worked on 32 bit Ubuntu, the problem came up when I foolishly decided to try it on Ubuntu x64. I will give your suggestion a try as well and tell you the results.

---

### Post by blueturtl on 2007-10-28
> the problem came up when I foolishly decided to try it on Ubuntu x64

So you have Ubuntu 64-bit edition in use now? I'm surprised the game would run at all, given that it is a 32-bit software for a *different* 32-bit OS. :o

---

### Post by PmDematagoda on 2007-10-28
I understood that concept only after I tried it:(. Oh well, no problem now as I've reinstalled it , but thank you for your help blueturtl:).

---

