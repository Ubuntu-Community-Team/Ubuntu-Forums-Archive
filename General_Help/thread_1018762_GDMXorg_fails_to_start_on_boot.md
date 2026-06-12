---
title: "GDM/Xorg fails to start on boot"
date: 2008-12-22
forum: General Help
---

### Post by beno1990 on 2008-12-22
Ok, so I tried rebooting my laptop a little earlier, and when it starts back up it initiated an autofsck scan which reached about 55%, before halting with a busy hard disk for about a minute and then quitting the usplash to display a black screen with a flashing "_" prompt.

I tried rebooting, it just put me into autofsck again and then did the same. I tried rebooting into the live CD, assuming it was an error in the autofsck program, and renamed /etc/rcS.d/S30checkfs.sh and ./S30checkroot.sh to ./K30checkfs.sh and ./K30checkroot.sh (to remove them from the startup).

After this, the usplash would continue as normal to start the remaining services before disappearing and leaving me at the "_" prompt without starting GDM/Xorg.

I've tried rebooting back into the live CD to try to change a few things, to no avail.

I've tried adding "gdm &" to /etc/rc.local, which still does nothing, for example.

I don't want to have to reinstall the OS because backing up my data and reinstalling all of the programs I have would be more trouble than I'm hoping to go through.

---

