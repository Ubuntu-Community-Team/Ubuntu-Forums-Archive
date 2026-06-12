---
title: "Wine broke my fonts :("
date: 2005-11-06
forum: Desktop Environments
---

### Post by simplyw00x on 2005-11-06
I used Sidenet wine config script to install IE6 and I think it broke my fonts; everything (Firefox <pre> tags, notepad in Wine, Bluefish) that uses (I think) Courier New displays invisible text instead. This terxt can be copy/pasted to another program, and changing the font seems to solve this, but there has to be a better solution.

Any ideas?

---

### Post by Who on 2005-11-07
Try (and I do really mean _try_...I am not at an Ubuntu box now)

sudo dpkg-reconfigure xfs

At a console/terminal

My method for fixing this would be: find out which packages are crucial to the font system (Using synaptic's search) and then reconfigure them

If you have done lots of tweaking with your fonts you may want to think of a different approach, becuase the dpkg-reconfigure resets things to just post install values...

hth
Who

---

### Post by simplyw00x on 2005-11-07
> carl@ubuntu:~$ sudo dpkg-reconfigure xfs
Password:
Package `xfs' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xfs is not installed
:(

---

### Post by Who on 2005-11-08
I'm guessing this is my fault and that the package is not called xfs - I will look when I get home - in  the mean time, why not look in synaptic for a package with a name mightily similar to xfs and do the same thing with that - you may find it quicker than waiting for me to install breezy (my entertainment for tonight ):P and answer the Q....

---

