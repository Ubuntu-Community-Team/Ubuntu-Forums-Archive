---
title: "NTFS + TrueCrypt + rdiff-backup"
date: 2009-05-29
forum: General Help
---

### Post by HavocXphere on 2009-05-29
I've got a sript like this:
```
truecrypt /media/Data/VersionHistory/Pictures.tc /media/TrueCrypt/ -p ######
rdiff-backup /home/ms/Pictures/ /media/TrueCrypt/
truecrypt -d
```
With TC volume being located on a NTFS drive. The TC volume type is FAT.

And its giving me:
```
Warning: hard linking not supported by filesystem at /media/TrueCrypt/rdiff-backup-data

```
It *seems* to do what its supposed to, but the message has me a little worried since this is meant to be a backup.

I don't think I want hardlinking...I want straight copies of everything. So does the above message mean that it is making copies or just ignoring hardlinked files?

Same goes for the --no-hard-links option: What does it do when it does encounter a hardlinked file?

[And no, the pictures folder doesn't contain *that* kind of pictures.]

---

### Post by Soul-Sing on 2009-05-29
First i have got a question. Which version of truecrypt do you use?
( the newest version comes with more options.)

---

### Post by HavocXphere on 2009-05-29
> **leoquant said:**
> First i have got a question. Which version of truecrypt do you use?
( the newest version comes with more options.)
6.2

Got straight off their website.

---

### Post by HavocXphere on 2009-06-01
bump

---

