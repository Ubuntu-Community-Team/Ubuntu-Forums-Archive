---
title: "Totally reset Gnome/Unity settings"
date: 2011-06-24
forum: Desktop Environments
---

### Post by mikecrowe on 2011-06-24
Hi folks,

I think I've upgraded now from 10.04 to 10.10 to now 11.04, and I believe I have so much cruft in my system that it's become unstable.

I thought I could selectively rename certain folders in my root (such as .gnome, .gnome2, etc, while logged of (i.e. from a ctrl-alt-f1 console), but that really didn't seem to work.

Any power suggestions for something to try?  I'd prefer not to copy to external hard drive and re-install fresh.  However, I'm using KDE now for stability, as neither gnome nor unity will run well.

TIA
Mike

---

### Post by Ozymandias_117 on 2011-06-24
Then you didn't rename all the folders that you needed to. :)

Make sure you get .gnome* and .gconf* and look at what all is in .config as well as .local - That should be the majority of your config files.  If it STILL isn't reset, just move all your dot files to a folder, then move the ones you know you want back (Probably .themes .icons and .mozilla)

---

### Post by ankspo71 on 2011-06-25
Hi,
Try running the command 'top' in the terminal to see if you can spot anything unusual happening like something causing medium to high CPU, memory, or swap usage. Sometimes even the slightest amount of swap usage can slow my computer down to a crawl.

Since Unity and Classic Gnome are performing poorly, and KDE is not, then it might be something like compiz causing the trouble, or something else running in the background while in Gnome or Unity.

Hope this helps.

---

