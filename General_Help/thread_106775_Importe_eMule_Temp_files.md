---
title: "Importe eMule Temp files"
date: 2005-12-21
forum: General Help
---

### Post by ethx on 2005-12-21
My windows instalation was getting slower and slower and so I decided to install ubuntu linux.

I have some GB's of Temp emule files from my windows time, and now I want to use those Temp files with aMule, I've copied the Temp files to .aMule/Temp, but aMule doesn't load the files, it gives errors like these:

(...)
2005-12-21 17:40:39: Trying to load backup of met-file from 167.part.met.bak
2005-12-21 17:40:39: Failed to open /home/ethx/.aMule/Temp/167.part.met (Dilbert_-_2x10_-_The_Assistant.(DVD).VFUA.xvid.avi)
2005-12-21 17:40:39: Failed to open /home/ethx/.aMule/Temp/168.part.met (Dilbert_-_2x11_-_The_Return.(DVD).VFUA.xvid.avi)
2005-12-21 17:40:39: Trying to load backup of met-file from 168.part.met.bak
2005-12-21 17:40:39: Failed to open /home/ethx/.aMule/Temp/168.part.met (Dilbert_-_2x11_-_The_Return.(DVD).VFUA.xvid.avi)
2005-12-21 17:40:39: Failed to open /home/ethx/.aMule/Temp/169.part.met (Dilbert_-_2x12_-_The_Virtual_Employee.(DVD).VFUA.xvid.avi)
(...)

Am I doing something wrong ? Or in the worst case.. importing Temp files from eMule to aMule isn't possible?

---

### Post by ow50 on 2005-12-21
Never tried it myself, but the aMule wiki says it should work.
[http://www.amule.org/wiki/index.php/Migrate_from_eMule_to_aMule](http://www.amule.org/wiki/index.php/Migrate_from_eMule_to_aMule)

> Temporary files are compatible between eMule and aMule, so you only have to set the Temp dir inside aMule (and let it rehash all files) to have them newly available to download.

One possibility is that if you copied the files directly from Windows, the permissions might be off. Try running the following commands in a terminal
```
cd ~/.aMule/Temp
chmod 644 *
```
That would give read and write permissions for you and read permissions for groups and  others. That's the default on Ubuntu.

---

### Post by ethx on 2005-12-21
Thanks! The chmod did it!

Loaded aMule, and now it's rehashing the Temp files!

---

