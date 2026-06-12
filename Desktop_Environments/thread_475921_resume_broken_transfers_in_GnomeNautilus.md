---
title: "resume broken transfers in Gnome/Nautilus?"
date: 2007-06-16
forum: Desktop Environments
---

### Post by congyiwu on 2007-06-16
i used to use Archlinux with KDE, but recently decided to try Ubuntu w/ GNOME.    I liked the simplicity/transparency of Archlinux, and the features and configurability of KDE, but realized that I never gave Ubuntu or GNOME a fair chance, and decided to try both out.

So far, I like how things that should work out of the box tend to automagically work on GNOME.  The only "issues" I had were having to add a line to xorg.conf and manually install gsynaptics (for horizontal scrolling) and that the version of gparted on the installer and in repositories didn't support moving partitions (and the gparted GUI would permanently hang while resizing my old reiser3 partition, although the partition seemed to resize fine).

Anyways, on to the problem I'm having.  I transfer a lot of big files (movies, large archives) over ssh to a server that my friend is keeping.  I also do these transfers with a laptop over wifi.  In KDE, I could use konqueror to transfer these files, and if something went wrong, or I cancelled the transfer so I could turn off my laptop or whatnot, I could always resume the transfer later, whether I was copying or moving files.  This is because KDE saves the new file with a .part extension, and then removes the .part extension when the transfer is completed, so it can easily tell if part of a transfer has already been completed (brilliant!).

In GNOME, I can transfer files over ssh with VFS, but GNOME can't resume the .part files.  If I cancel a transfer, the new file gets deleted automatically, and I have to restart from scratch.  If my signal dies and the transfer fails, sometimes the transferred part is still there (but without a .part extension) and when I retry the transfer it rewrites the old stuff instead of resuming.

Is there a way to tell nautilus to resume file transfers? I looked around in the natilus config and the gconf-editor, but couldn't find anything...  Also, is there a way to make the transfer dialog show the size of the transfer and the current transfer rate?

Thanks

---

### Post by scrooge_74 on 2007-06-24
The other day I made a full copy of my /home folder to another machine using grsync  and at some point the laptop when to sleep, but the transfer resume with no problema after

---

### Post by congyiwu on 2007-06-28
Thanks for replying.
rsync is really nice, especially for updating remote copies of large websites where only a few files change at a time (not sure why I never tried it earlier).  I decided I was more of a KDE guy though (been using it for a year now), and switched to Kubuntu.

---

