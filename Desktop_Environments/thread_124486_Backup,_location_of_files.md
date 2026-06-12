---
title: "Backup, location of files"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Bucho1978 on 2006-02-01
Hi,

I just bought an external USB disk.  Now I want to use it as a backup device.  My thoughts are to make a small script that copies the things I want to that disk.  Therefor I would need the location of some files.

- inbox of evolution
- contacts of evolution
- tasks of evolution
- kalendar of evolution
- bookmarks of Firefox

Thx in advance

---

### Post by el3ktro on 2006-02-01
Open up the Gnome file manager in your home dir and press Ctrl+H, this will show you all hidden files and dirs. Hidden files and dirs always start with a . (dot). You'll find a dir .evolution, and one called .mozilla I think, you can copy both to your USB stick. I recommend writing a script using rsync, this way you can keep your backup copy in sync with your local directories easily.

Tom

---

### Post by Bucho1978 on 2006-02-01
thx for the quick reply.

---

