---
title: "Switching to Kubuntu"
date: 2006-01-13
forum: General Help
---

### Post by shane2peru on 2006-01-13
Hey, I have been using Ubuntu for a while now.  A few times I have installed KDE desktop and found many problems because Ubuntu was the default install.  Plus, I just run out of room.  I have backed up my Ubuntu on an external hdd, and am really looking into installing Kubuntu.  I also backed up my /home .  When I install Kubuntu am  I going to have to configure everything again?  Will I be able to restory my /home dir and expect anything to work right (FireFox, Thunderbird, BibleTime/Gnomesword  Wine etc..)  Thanks for the help.

Shane

---

### Post by aysiu on 2006-01-13
You say you backed up your /home--does that mean you didn't create a separate /home partition? If so, install Kubuntu fresh and then copy your /home folders over one at a time, testing functionality one at a time. For example, after you install Firefox, copy over ~/.mozilla and see if it works. Then, after you install Thunderbird, copy over ~/mozilla-thunderbird and see if it works.

It should all work.

If you have a separate /home partition, just install Kubuntu to the other partition and set your /home partition to mount at /home and not reformat.

---

### Post by shane2peru on 2006-01-13
I do have /home in a separate partition, but was concerned that it may mess things up if I left it.

Shane

---

### Post by Brando569 on 2006-01-13
nope shouldnt screw up anything, some programs might not work (cuz they werent installed initially, install them and theyll work fine) other then that all your personal prefs should be saved, since thats whats stored in your home. thats one of the major things i love about linux compared to windows

---

### Post by shane2peru on 2006-01-13
I should be able to delete the ~/.gnome type directories right?  That should slim down my /home directory size.  Right?  Thanks.

Shane

---

### Post by aysiu on 2006-01-13
[QUOTE=shane2peru]I should be able to delete the ~/.gnome type directories right?  That should slim down my /home directory size.  Right?  Thanks.

Shane[/QUOTE] I'd hold off on doing that until you're sure they don't affect any Gnome apps you may be using in Kubuntu.

---

### Post by shane2peru on 2006-01-14
Actually, well I already did.  I have them in backup so it isn't to big of a deal.  I figure if I delete them first thing, then if I install something that would use them it will create the folder for me.  I deleted the folders like .gconfig  .gnome  .gnome2  .gnome-private  I think that is it.  

Shane

---

