---
title: "Write protected files from CD"
date: 2005-06-23
forum: Desktop Environments
---

### Post by RadixLecti on 2005-06-23
I've just transferred a few mp3's from dvd to my reinstalled ubuntu, and as always, I get annoyed at the automatic write-protection that gets slapped on anything from a cd/dvd. Is there a way of disabling this?

---

### Post by nocturn on 2005-06-23
[QUOTE=RadixLecti]I've just transferred a few mp3's from dvd to my reinstalled ubuntu, and as always, I get annoyed at the automatic write-protection that gets slapped on anything from a cd/dvd. Is there a way of disabling this?[/QUOTE]

Does this also happen when copying from the command line?
I know cp has an option to explicitly maintain the permissions, so by default they should be good.

---

### Post by afonic on 2005-06-23
Well yes files in CDs are read-only and cp maintains the permissions.

It just a simple command from shell to make them writeable (I guess your trouble is multiple files in multiple folders?).

Just chmod -R 755 foldername or whatever permission you want.

---

### Post by RadixLecti on 2005-06-23
Ah, that helped. Thanks.
Although I normally use two nautilus windows. CD there, destination there, drag and drop, et voilá. (yes, I'm hopelessly stuck in GUI-land. That's all right though, I quite like it there. Nice weather, and good beer.)

---

