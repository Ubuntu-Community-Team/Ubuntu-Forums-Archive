---
title: "adding other folders to Places -&gt; Computer?"
date: 2005-06-17
forum: Desktop Environments
---

### Post by bigcletus on 2005-06-17
Is it possible to add another folder/location to the Computer folder under Places?  I would like my NTFS partition (that gets mounted at boot under /media/windows/) to appear in this folder.  Thanks for any suggestions :)

---

### Post by kastorff on 2005-06-17
Try creating a symlink to the mount point in the top level of your home directory. That works in Gentoo.

---

### Post by bigcletus on 2005-06-18
thanks for the info, but that didn't do the trick.  What I did do was add the following lines in my /etc/fstab:

```

dev/hda1       /media/windows/hda1  ntfs    umask=0222      0       0
dev/hda5       /media/windows/hda5  ntfs    umask=0222      0       0

```

then the icons not only appeared in System -> Computer, but also showed up on my Desktop.  Works pretty good.

---

### Post by kastorff on 2005-06-29
Well, it didn't work for two reasons:
1) I misread your question and was thinking of adding folders to that menu, and not volumes.
2) I was wrong about the mechanism that manages those places; my folder was there not because I had a symlink at the root of my home directory, but because I'd added it as a bookmark in the Open File... dialog box.

So, all in all it was a pretty sorry response on my part. Glad you got it fixed, and I hope this will help others who might want to add a folder to that menu.  :-)

---

