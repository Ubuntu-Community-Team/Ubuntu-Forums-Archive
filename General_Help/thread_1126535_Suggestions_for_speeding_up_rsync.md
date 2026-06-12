---
title: "Suggestions for speeding up rsync?"
date: 2009-04-15
forum: General Help
---

### Post by Scarfy on 2009-04-15
I use a shell script to sync my laptop's music collection with my MP3 player, as follows,

```
MNTDIR="/media/disk"
SOURCE="~/Music/Singles"

echo "Syncing music from '$SOURCE' to '$MNTDIR'..."
rsync -v -a --no-g --delete $SOURCE $MNTDIR
```

The thing is that the rsync call is quite slow. Sure, in this case there is 1.7GB over 338 files to check, but it takes about 5 or 6 minutes. I'm sure it shouldn't take as long as that.

Any tips as to flags or parameters I can pass to rsync to make the process fast? It is copying MP3s and OGGs over, so all binary files.

---

### Post by bapoumba on 2009-04-17
Moved to General Help.

---

