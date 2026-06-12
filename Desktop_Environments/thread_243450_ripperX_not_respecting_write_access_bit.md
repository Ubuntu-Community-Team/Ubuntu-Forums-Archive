---
title: "ripperX not respecting write access bit?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by xfred on 2006-08-25
I've just run into a weird problem.  A while back I used ripperX to rip a few cds to wav (with humungous cheap hdds, I really couldn't see the point of compression for a few cds).  Anyhow, just recently I wanted to convert to mp3 to use elsewhere, while keeping the wavs... so I loaded up ripperX, told it to use existing wavs (and not delete them when done) and set it going.

First cd worked fine.  Next cd, though, I forgot to select tracks, and the f***ing thing wiped all the wavs (without even asking first... not exactly polite imo).  Subsequently, as a precaution I set all of the wavs to read only (disabled all write access using the properties tab).  All was fine until I *again* forgot to select tracks a few cds later... and it proceeded to wipe the tracks *which were marked read only*.

So what gives?  I thought read only meant just that... no-one (program, person or other) could write until I re-enabled write access to the files.  And I'd always assumed that this was an os level thing, so non-trivial to bypass.

Anyhow, I guess my question is... how to I mark files to prevent ripperX (or any other program for that matter) from deleting them?

---

### Post by RAOF on 2006-08-25
It's not obvious.  The permission you set on the file meant that programs couldn't write to it (for example, replacing it with all 0's or something).  However, that doesn't stop a program **deleting** the file - that's not the same as writing to it.

To stop files from being able to be deleted, you actually have to remove write access to the **directory** they live in.  It sort of makes sense when you think that you write files to a directory, and deleting a file from a directory changes the directory, not the file.  Sort of :)
Think of create/delete as the things you can do with write permissions to a directory.

You can do all sorts of interesting and wierd things with directory permissions.  Like being able to create/read/write/delete delete files, but not be able to find them, or to list the directories they're in.

---

### Post by xfred on 2006-08-28
Ahh, thanks.  That kind-of makes sense in a round-about way.

cheers

---

