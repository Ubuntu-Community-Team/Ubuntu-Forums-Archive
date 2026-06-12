---
title: "Is it possible to recover deleted images from a specific folder?"
date: 2009-05-07
forum: General Help
---

### Post by jobbesat on 2009-05-07
under Ubuntu Jaunty

Thanks a lot in advance

---

### Post by Saghaulor on 2009-05-07
Did you send them to the trash or did you delete them directly?

Because if you sent them to trash without deleting them, then you can just open the trash bin and recover them.

If you deleted them, I believe that they can be recovered, I'm just not sure how.

---

### Post by cdenley on 2009-05-07
There isn't any simple undelete function for ext3. Data about deleted files are overwritten when they are deleted, but the file's actual data is simply marked as unused and will be overwritten eventually. You can recover the file, but there is no way to know where to look for it since the file's name and path no longer exist. For recovering deleted files of a common file type, you can try the photorec command from the testdisk package.

---

### Post by jobbesat on 2009-05-07
Thanks. Infact I already tried photorec and recoverjpeg, but there's no chance to select a single directory, they serach inside the entire partition and that can take a long time.

---

### Post by cdenley on 2009-05-07
> **jobbesat said:**
> Thanks. Infact I already tried photorec and recoverjpeg, but there's no chance to select a single directory, they serach inside the entire partition and that can take a long time.

It would be impossible to select a directory, as I tried to explain, since deleted files have no directory, and the data which indicated what directory a deleted file was in no longer exists. Photorec is the best solution you will find. You are looking for raw data now. Filesystems, directory structures, and filenames are now useless for finding your file.

---

