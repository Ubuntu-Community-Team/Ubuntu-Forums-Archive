---
title: "Moving to Trash deletes immediately"
date: 2010-09-15
forum: Desktop Environments
---

### Post by dgermann on 2010-09-15
Hi--

Under 8.04 lts moving a file to Trash under Gnome/Nautilus resulted in the file being moved to the Trash directory, from where I could then delete it. It was an extra layer of protection against mistakes.

Now when I right click on a file and choose move to Trash, it deletes immediately without the protection.

I see no way to turn it back on. Is this a change in the way Nautilus is meant to work, or is there a switch someplace to put it back?

Thanks!

---

### Post by opticyclic on 2010-09-18
[http://ubuntuforums.org/showthread.php?t=180635](http://ubuntuforums.org/showthread.php?t=180635)
Check you haven't accidentally set the flag.

---

### Post by dgermann on 2010-09-19
opticyclic--

Thanks for helping me!

That does not seem to be it--I did not even know this program existed. But it was checked properly and unchecking and checking again did not make a difference.

Any other thoughts?

Thank you!

---

### Post by opticyclic on 2010-09-27
Just remembered something else that I did when I had a separate partition mounted.
Had to modify the fstab
[http://ubuntuforums.org/showpost.php?p=9536737&postcount=7](http://ubuntuforums.org/showpost.php?p=9536737&postcount=7)

---

### Post by dgermann on 2010-09-27
opticyclic--

I don't think that is the problem--my fstab seems similar to yours, although I am using uid=doug instead of uid=1000, and the ownership is doug:data not doug:doug as yours is.

However, I think you are pointing me to a clue. I checked a couple of directories where I had been deleting things and found some .trash-1000 and .Trash-1000 directories--and in them seem to be many of the files I had been deleting, thinking they were bypassing the trash bin--large files too, some of them 30+ megs!

So it appears to me like the trash bin is looking in the wrong directories to find the deleted files. Any idea how this could be fixed?

Thanks! You are pointing me toward some clues, opticyclic!

---

