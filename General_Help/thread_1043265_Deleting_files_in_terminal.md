---
title: "Deleting files in terminal"
date: 2009-01-18
forum: General Help
---

### Post by winrowc on 2009-01-18
I have about 250 folders from a data recovery and want to get all the mp3 files together and delete all the rest. How would I do this in the terminal? I don't want to have to go into each folder individually and delet things.

---

### Post by hal8000 on 2009-01-18
This command will work:
mkdir ~/recovered
find /home/tux/recovered -name '*.mp3' -exec cp {} ~/receovered \;

Hope that helps

---

### Post by 505 on 2009-01-18
The above command would find all mp3's and then delete them. The OP wants to delete all the rest, not the mp3's. Safest bet is to copy all mp3's first, then delete the folder. You can use the command hal8000 said, but give a copy command after it:

find /home/tux/recovered -name '*.mp3' -type f | xargs -i cp {} /home/tux/music

The first part finds all files with mp3 in the name (only files, because of "-type f"). Each result is copied to /home/tux/music You will loose the folder structure in recovered if you do it this way. After copying, you can delete the recovered folder.

---

### Post by heindsight on 2009-01-18
As i understand, the intent is to delete everything *except* the mp3 files.

what you could do is:
```
find /home/tux/recovered -type f -not -name '*.mp3' -exec rm \{\} \;
find /home/tux/recovered -type d -exec rmdir \{\} \;
```

this would delete all but the .mp3 files and then remove all empty directories.

You could also do something like:
```
mkdir /home/tux/recovered_mp3
find /home/tux/recovered -name "*.mp3" -exec mv \{\} /home/tux/recovered_mp3 \;
rm -Rf /home/tux/recovered
```
which would move all the recovered *.mp3 files into the newly created recovered_mp3 directory before completely deleting everything else you recovered.

however you do it, be careful. the rm command permanently deletes the files they're not just moved to a trash bin. so make sure you don't accidentally delete something you wanted to keep...

---

### Post by hal8000 on 2009-01-18
> **505 said:**
> The above command would find all mp3's and then delete them. The OP wants to delete all the rest, not the mp3's. Safest bet is to copy all mp3's first, then delete the folder. You can use the command hal8000 said, but give a copy command after it:

find /home/tux/recovered -name '*.mp3' -type f | xargs -i cp {} /home/tux/music

The first part finds all files with mp3 in the name (only files, because of "-type f"). Each result is copied to /home/tux/music You will loose the folder structure in recovered if you do it this way. After copying, you can delete the recovered folder.


Dank u wel 505.
Sometimes I answer too quickly, changed post and modified command.

---

### Post by winrowc on 2009-01-19
Thanks worked perfectly!

---

