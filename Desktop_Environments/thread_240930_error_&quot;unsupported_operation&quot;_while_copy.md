---
title: "error &quot;unsupported operation&quot; while copying"
date: 2006-08-21
forum: Desktop Environments
---

### Post by BoomAM on 2006-08-21
Hi.
Does anyone have any idea on how to get rid of that error?
After restoring my partition table as [here]("http://www.ubuntuforums.org/showthread.php?p=1405612#post1405612"), ive used a LiveCD to make a mount point for my Ubuntu partition, so i can backup my data off it. Problem is, that i keep getting the error seen in the title.

Any ideas?

##EDIT##
Some files copy fine, like jpgs, but im trying to copy my evolution folder, and i get:
```

Error whie copying.
"/home/Ubunt...alview.xml" cannot be ccopied because you do not have permissions to read it.

```

---

### Post by BoomAM on 2006-08-21
Ive worked out that i need to change the permissions for the 'boomam home' folder on my old Ubuntu partition.
What command is it to change the permissions for a folder and its contents?

This command:
'chmod a+x .evolution' 
changed the permissions for the evolution app folder only, not its contents.
What command is it to change an entire folder & its contents?

---

