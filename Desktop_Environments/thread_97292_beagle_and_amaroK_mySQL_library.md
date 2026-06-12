---
title: "beagle and amaroK mySQL library"
date: 2005-11-30
forum: Desktop Environments
---

### Post by royg1234 on 2005-11-30
Is there a way to make beagle index amaroK's mySQL music library?  I currently have all my music files in a FAT32 folder.

---

### Post by RAOF on 2005-11-30
Beagle doesn't support indexing the library, no, but it should be able to index all the actual files, even if they are on a FAT32 partition.  It can extract the metadata (tags) from most multimedia file types, and will index them.

---

### Post by royg1234 on 2005-12-01
Thanks.

That's interesting.  But I think I remember reading somewhere that Beagle works only with certain filesystems, or some of its features don't work with FAT32.

---

### Post by RAOF on 2005-12-01
Quite true - you don't get xattr support for FAT32.  xattr basically allows you to store arbitrary metadata alongside each file, and beagle uses this to mark what files it has already indexed, whether they have changed, etc.  It will still work without FAT32, but it's slower (to index), basically.

---

