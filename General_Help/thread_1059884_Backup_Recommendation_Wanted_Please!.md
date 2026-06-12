---
title: "Backup Recommendation Wanted Please!"
date: 2009-02-04
forum: General Help
---

### Post by uv_goth on 2009-02-04
Looking for a program to do my backups with and hope someone can help. :)

I have a Freecom 160GB external HD for backing up my data files which are all stored on a seperate partition as I dual-boot XP and Kubuntu.

Are there any application that will allow me to backup without having to either copy everything in total or check which are newer files?

ie. Is there a way to only overwrite if files to be copied across is newer?

---

### Post by vanadium on 2009-02-04
rsync does that. With the command

rsync -a <source> <destination>

you will synchronize <destination> with <source>, e.g.

```

rsync -a /home/vanadium/documents /media/USB/

```

will create or update a directory "documents" on the USB drive.

* Add the option "-v" to have more feedback of what has been done
* Add the option --del to delete files in the destination that do not anymore exist in the source (mirrorring)
```

rsync -av --del /home/vanadium/documents /media/USB/

```

---

