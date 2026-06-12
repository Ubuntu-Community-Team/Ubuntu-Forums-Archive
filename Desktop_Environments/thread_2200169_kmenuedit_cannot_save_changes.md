---
title: "kmenuedit cannot save changes"
date: 2014-01-17
forum: Desktop Environments
---

### Post by scottbomb on 2014-01-17
I have 2 programs sitting in the "Lost and Found" folder on the Kicker Menu (I use classic view if that matters). I right-clicked the menu and choose "Edit Applications". kmenuedit launches and I'm able to move the launchers to their appropriate folders. I then click save, and get this message: 
```

Menu changes could not be saved because of the following problem:
Could not write to /home/$USER/.config/menus/applications-kmenuedit.menu

```
So... what exactly is the problem? This dialogue doesn't say.
I try launching kmenuedit with gksu and I am able to save my changes, except they don't actually take effect. The program says "updating system configuration" but nothing actually changes, even after a reboot.

It also seems that when I run it under gksu, it saves the changes to its own file somewhere because when I launch it again later, it has the saved changes from before. In other words, it still thinks I successfully moved those launchers last time but it never actually changed in the menu. 

I hope this makes sense!

---

### Post by scottbomb on 2014-01-17
Not fixed but I found a workaround. kmenuedit attempts to access /home/$USER/.config/menus, however, that folder is owned by root and had read/write permissions only for root. I did
```
sudo chmod 777 /home/$USER/.config/menus

```
and I was then able to launch it (without root) and save changes as it should. It actually made the changes too. I'll mark the thread as solved but will consider filing a bug against kmenuedit.

---

