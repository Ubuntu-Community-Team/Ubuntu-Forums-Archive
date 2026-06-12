---
title: "Let thunar and nautilus share emblems"
date: 2007-07-28
forum: Desktop Environments
---

### Post by vexorian on 2007-07-28
So, nautilus is awesome for things like sftp and ssh, but probably too slow for your own hard drive. So I began to like thunar but the issue is that it doesn't know about the emblems I set through nautilus (including the desktop ones) so it is pretty bad... 

So perhaps there is a way to make thunar use nautilus' emblem data, or copy it to thunar or something like that?

---

### Post by Enohc on 2007-08-09
I just spent some time trying to share emblems between thunar and nautilus. No luck

Nautilus stores emblems's in xml files in the folder $HOME/.nautilus/metafiles/
Thunar uses a TDB database file ($HOME/.cache/Thunar/metafile.tdb) to do the same thing.

So they have the same information (or at least i think it should be the same) in two different places in two different formats :(

Maybe there is some kind of converter between  TDB database files and xml to keep them syncronized but I give this up.

---

### Post by vexorian on 2007-08-09
ow that's pretty lame, so in order to replace nautilus with thunar I'll have to remake all emblems but the desktop emblems will always need some syncing.. -_-

---

