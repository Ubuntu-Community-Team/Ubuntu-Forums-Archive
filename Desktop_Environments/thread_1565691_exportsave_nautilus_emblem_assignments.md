---
title: "export/save nautilus emblem assignments"
date: 2010-09-01
forum: Desktop Environments
---

### Post by phoenigs on 2010-09-01
Hi,

my problem is as follows:
to reinstall my os, i want to backup some of my personal settings.
for work i used emblems in nautilus to flag files i already processed (manually).
now, i do not find any possiblity to back up the emblem-assignments. 
from older threads i figured out, that these assignments were in an .xml file in the ~/.nautilus/metadata folder, which is empty since newer versions of nautilus.
i also tried to get some useful information out of the 
.local/share/gvfs-metadata/* files, but i did not succeed with this approach either (just used the "strings" command on them).

any ideas?

edit: i'm aware, that i could write a script reading the metadata of the files via gvfs-info. the problem is, i cannot access the files from home, only at work via windows share.

---

### Post by ariadacapo on 2010-09-03
I second that question... I would love to know where this emblem metadata is stored.

I changed my hard drive and lost all the emblems on my data ; yet they are still visible on the mounted backup copy.

I spent hours searching forums, documentation and the Greater Internets, without success...

---

### Post by phoenigs on 2010-09-03
Wrote a litte script now to export emblemed files (but just only for one emblem and one directory, according to my needs).
If you are a bit into scripting, should be not that difficult to transfer the emblem attribute via gvfs-info and gvfs-set.



(Solved my problem by going to my workplace and stored emblemed filenames via my script, now I do not use them anymore for this reason).

Good luck for you...

---

### Post by phoenigs on 2010-09-03
Ah, I thought a bit further about the gvfs thing, and as you described you have the emblems still on the original backup.
So you could use "gvfs-copy" to copy the files from the backup to your new harddisk. This should copy the attributes, too. (Cannot test that, switched to another distro...)

---

### Post by ariadacapo on 2010-09-04
> **phoenigs said:**
> Wrote a litte script now to export emblemed files (but just only for one emblem and one directory, according to my needs).
If you are a bit into scripting, should be not that difficult to transfer the emblem attribute via gvfs-info and gvfs-set.

Thanks, using gvfs-info is one step forward (gvfs-set does not seem to exist for me).

Would you mind sharing your script, or perhaps just a few command lines ?

---

### Post by phoenigs on 2010-09-04
Ah, should be gvfs-set-attribute (hadn't the exact command in mind).
Was a bit of java code (not good at script languages :( ), but deleted it already. Didn't gvfs-copy work?

---

### Post by ariadacapo on 2010-09-12
> **phoenigs said:**
> Ah, should be gvfs-set-attribute (hadn't the exact command in mind).
Was a bit of java code (not good at script languages :( ), but deleted it already. Didn't gvfs-copy work?

Thank you for your time phoenigs.
gvfs-copy did not suit me. My files have changed since the backup and I did not want to risk overwriting them.

My intent was to export gvfs information from the backup to a text file, and then use gvfs-set-attribute to "write" this information to my current files.

In the end the risks and hassle were too large to bother. I set my labels manually again. With the time I know I saved, I had a walk outside ;-)

---

