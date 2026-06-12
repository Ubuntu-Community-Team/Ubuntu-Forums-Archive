---
title: "Symbolic link behaviour in Gnome/Nautilus"
date: 2008-06-29
forum: Desktop Environments
---

### Post by rosbif on 2008-06-29
I create a symlink on my desktop to a folder (say MyFolder).  If I click on the link, Nautilus opens with the hierarchy shown as Desktop < MyFolder, rather than MyFolderParentParent < MyFolderParent < MyFolder, in other words, as if I had navigated to MyFolder from a Nautilus window, which is what I want.  Is it possible to change the link behaviour? I'm on Hardy.

---

### Post by vanadium on 2008-06-29
You are seeing the power of Linux softlinks. They behave exactly like physical directories and thus allow you to organize the system the way you want and to access the same item from different access points. For limited, Windows like "shortcuts", use Gnome Launchers instead.

---

### Post by rosbif on 2008-06-29
Hmmm, that would be fine if the Create Launcher dialogue actually allowed you to enter a folder.  Unfortunately, it doesn't complete until you select a file.  Yes, you can type in the path, but that kinda misses the point of having a GUI with selection.

---

### Post by vanadium on 2008-06-29
That is a one time task, so it is not as bad as it sounds. You actually will have to enter 'nautilus "path-to-the-directory"' as the command. One trick is to select a file in the target directory through the Browse button, then add "nautilus" in front and delete the filename to leave the path there.

I agree with you that this could be better for a desktop environment as mature as gnome.

---

