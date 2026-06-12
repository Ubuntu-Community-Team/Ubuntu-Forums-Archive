---
title: "How to use --exclude variable with TAR or RSYNC"
date: 2009-02-28
forum: General Help
---

### Post by sofasurfer on 2009-02-28
Normally a command looks like this...
 tar  cvpzf /home/backup.tgz --exclude=file1 --exclude=file2 --exclude=file3 /home

When writing a script you use variables like...
FILESTOINCLUDE=/home /usr /root

But how do you use a variable for --exclude?
Each excluded file or directory must be individually written as "--exclude=suchandsuch". 
Is the variable written the same as when you use included files? When ever an example is given, only one file is excluded in the example.
Is the variable still written as...
FILESTOEXCLUDE=/file1 /file2 /file3?

My God this is hard!

---

### Post by Mozai on 2011-03-30
When I'm dealing with a list when commands only allow one-at-a-time, I will cook the list into a long complicated string.  Ah, easier to show you than to describe it.

#!/bin/sh
FILESTOEXCLUDE=" alpha beta delta
  gamma epsilon "  # quoted strings for this purpose can have line breaks in them
EXCLUDEPARAMS=""
for f in FILESTOEXCLUDE; do
  EXCLUDEPARAMS="$EXCLUDEPARAMS --exclude=$f"
done
rsync $EXCLUDEPARAMS /usr/local/source /mnt/device/destination

Hope that helps.

---

### Post by SeijiSensei on 2011-03-30
Use --exclude-from and put the patterns into a file.

---

