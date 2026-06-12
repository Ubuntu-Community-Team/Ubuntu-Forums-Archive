---
title: "Auto-mounting Directorys"
date: 2009-03-15
forum: General Help
---

### Post by Clarkey252 on 2009-03-15
Hello people of Ubuntu land, I was wondering if anyone could lend a hand.

I've just installed Ubuntu on my computer and now have a dual boot with windaz, my music is currently sitting on my second hard-drive and I would like it to mount itself to my music folder in /home/myuser/music

I can get the drive to auto-mount but not the specific folder. Is there anyway i can do this?

Thanks for reading,
Clarkey252

---

### Post by taurus on 2009-03-15
Your best bet is to mount that windows partition (ntfs) to /media/music and then create a link from your $HOME, ~/music, pointing to /media/music.

---

### Post by vanadium on 2009-03-15
What do you mean with "I can get the drive to automount"?

Anyway, in linux, it is easy to access your data, wherever it lives, from a location of your choice: use a symbolic link or symlink. Here is how:

* Open the directory where your Music folder lives in one nautilus window
* Open another nautilus window in your home directory.
* Press Ctrl+Shift and drag "Music" from the first nautilus window to the second. Release the mouse button.
* This creates a "link to Music" folder in your home. Rename it to "Music" (or "music") and you are all set: you have one-click access from within your home directory to your music.

For practical purposes, such a symbolic link behaves and feels like a regular directory.

---

