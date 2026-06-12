---
title: "Recover files from deleted EXT4"
date: 2009-05-29
forum: General Help
---

### Post by smileboot on 2009-05-29
I did somthing really dumb and acidently installed a ext3 install over my ext4 (after deleting it). Dont ask me why or how i was just dumb is all.

What im wondering is there a way to search the raw hardrive for files on the old EXT4 partion that now no longer exists. I know if it was an ntfs filesystem even if id deleted and written over a few times i could still maybe recover files.  If theres a way to recover anything. 1 or 2 files are irreplacable (but ill live if i dont have em).

I have tried Testdisk but since an ext4 was overwritten with ext3 system. It only detects the most recent files/journal and for some reason wont even let me browse the more recent files.

Any suggestions  even a windows app would be appreciated at this point.

---

### Post by not a pipe on 2009-05-29
I've had some success with photorec ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)), but that would just dump anything it finds rather than letting you search the drive. 

The sleuth kit ([http://www.sleuthkit.org/](http://www.sleuthkit.org/)) is the only other thing I've tried. It might be able to do what you want. It's a bit more complicated than photorec, so I didn't use it much.

---

