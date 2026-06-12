---
title: "Intrepid freezes on beige screen, even after re-install"
date: 2009-02-11
forum: Desktop Environments
---

### Post by tgyorgyi on 2009-02-11
What happened so far: I've been running Intrepid since October. After changing screen resolution in order to be able to use a projector, Ubuntu 8.10 freezes on the beige screen after login. Apart from changing the resolution I did not do anything, no updates, no installs, whatever. 

I tried some of the suggestions in the forum but none worked, so I reinstalled 8.10 from the Live CD. My /home directory is on a separate partition, so that has remained unchanged with all of its contents.

After re-installing, the same happened: freeze on the beige screen, with the coursor gone. 

Next I tried a custom 8.04 live cd that I made with Remastersys. This time the install went fine, and Ubuntu worked as long as I stayed with Hardy. But when I hit the version update button... once the update was finished, and I've restarted Ubuntu, 8.10 froze at the beige screen just like before.

Any help would be highly appreciated, my laptop is my livelyhood, I miss it greately. 

The laptop is an FSC Amilo L.

---

### Post by malachi1990 on 2009-02-11
Try clearing out your config files for gnome.  Because of the change in the setup of xorg.conf between intrepid and previous versions of ubuntu, the new setup may be what's causing your problem.

---

### Post by tgyorgyi on 2009-02-11
Thank you. Which would be those files exactly? And: would I have to reinstall after cleaning those files, or would they be re-written when they are found empty upon the next startup?

---

### Post by malachi1990 on 2009-02-11
I would guess that the right files would be in your home folder.  tell nautilus to show hidden files (Ctrl+H), and then delete the .gnome2 and .gnome2_private. This may break packages, as this is related to a desktop environment, and not just a wm.

My experience with other window managers is that the files will be rewritten when you log in. If this doesn't work, I don't know what to tell you except to poke around in /etc.  Though it sounds like you didn't keep them on a separate partition.

So try this at your own risk.  I personally back up my files via an external, so that I don't carry my conf files over versions of ubuntu (especially between 8.04 and 8.10).  Ify you can, you may want to try this as well.

---

### Post by tgyorgyi on 2009-02-12
Thank you, and also for the backup tip. My /home folder is on a separate partition, but the rest of Ubuntu is together. For now I have downgraded to 8.04 because I need to meet a couple of deadlines and need a functioning OS, but I will try to upgrade again this weekend, and then try your suggestion. The strange thing is that I've used 8.10 without a problem since October, and the problem did not show up immediately after an update...

Cheers,
Györgyi

---

### Post by malachi1990 on 2009-02-18
It depends on what you're updating, if a kernel or Xorg update makes a call that is incompatible with the version shipped with Hardy, that could lead to what you experienced, but I can't say for sure (since I dont't know much about that area).

---

### Post by tgyorgyi on 2009-03-01
Hi, I tried removing the two directories before starting the upgrade. Same result, after upgrade when I restart, Ubuntu hangs on the beige screen, cursor arrow disappears, HDD stops spinning aside from a flicker of movement every now and then. The strange thing is, that I was running Intrepid fine since October, and I was cut off from the Internet when this happened, so Intrepid was functioning properly since the last update, the only new issue was trying to hook up the projector (Which by the way worked plug-and-play whith this laptop while I was running Hardy. However, now it would not work even with Hardy).

Since I had the same result when I did a clean install of Intrepid (also did not use to be a problem), I am quite at a loss. I found a lot of unanswered projector and resolution-related posts in the forum, so I am not very hopeful, but if there is anybody out there with a further suggestion, don'"t hesitate to write.

Thank you.

---

### Post by utnubuuser on 2009-03-01
Hi - if it's your configurations:> [http://ubuntuforums.org/showthread.php?t=1060406](http://ubuntuforums.org/showthread.php?t=1060406)

---

### Post by tgyorgyi on 2009-03-01
Thank you, unfortunately this is not helping either... Also, the other post writes about messed-up desktop... but I'm not getting any desktop whatsoever, this is more like a freeze, as the only way to have an effect on my laptop after this beige freeze is a hard reset.

---

