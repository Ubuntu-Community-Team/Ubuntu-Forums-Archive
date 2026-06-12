---
title: "Transfering files to FAT32 usb drive"
date: 2009-05-12
forum: General Help
---

### Post by yme on 2009-05-12
Hello,

I have a huge collection of folders of PDF material that I have amassed while I have been an Ubuntu user. I now need to make copies of this to give to colleagues who use Windows. 

The problem is when I am copying many of these files have names which are accepted by Ubuntu and not by Windows. I sat for an hour last night clicking 'skip' everytime one came up (surprsingly there is no 'skip all' feature). 

I now have 90% of the files copied but don't know what has been missed (the full name is not given in the prompt box even if I had time to note them all down). 

Is there no way I can copy and Ubuntu automatically rename the files by dropping the characters disallowed by FAT32? In Windows if you try and save with a disallowed filename it does this as default.

Thanks,

Yme

---

### Post by kanikilu on 2009-05-13
You could use **rename** and regex to do a batch rename of these files. If feasible, copy these files to another directory first, also you can use the **-n** option on rename to do a "dry run" without changing anything.

The following will rename all files in the *current* directory, removing these characters: **\ : * ? " < > |**

```
rename 's/[\"\\\<>\:\*\?\|]//g' *
```

I don't know if there are more characters that are not allowed on FAT32, so you might need to add some if necessary...

If there are sub-folders, you'll probably need to use **find** or a combination of the two, but that's starting to get a bit over my head...

---

