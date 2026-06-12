---
title: "Cracking write-protected .ace archives?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-01-15
I am trying to unace an .ace archive. The error message I get is as follows: 

```
UNACE v2.2     Copyright by ACE Compression Software       May  9 2002 10:59:42

processing archive \..ule/Incoming/Jazzkantine.ace
Working: Creating listfile. Please wait.
Working: Reading archive. Please wait.
created on 15.6.2002 with ver 2.0 by
*UNREGISTERED VERSION*
  extracting Jazzkantine/heiss & fettig/playlist.m3u
Error: Could not create directory:
 \..kantine/heiss & fettig
Error: Could not create destination file: \..tig/playlist.m3u
 Disk might be write-protected.
```

Is there any way to crack this or to work around it?

Gabriel

---

### Post by stoffe on 2006-01-15
It doesn't look like it has anything to do with "cracking" anything, it looks like you don't have permissions to create directories and/or files where you are trying to unpack the archive to.

---

### Post by glennph on 2008-04-16
Had the same problem.. 

**'unace x file.ace' ** instead of 'unace e' solved my it for me..

---

