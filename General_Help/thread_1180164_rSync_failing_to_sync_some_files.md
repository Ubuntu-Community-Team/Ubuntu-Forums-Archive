---
title: "rSync failing to sync some files"
date: 2009-06-06
forum: General Help
---

### Post by codeking on 2009-06-06
I'm running rSync (Actually, the GUI, grSync) to keep my MP3 (iRiver h340) in sync with my music. (On an NTFS partition)  It runs fine for the most part, but fails on 20 or so songs.  Heres the error output:

> rsync: recv_generator: mkdir "/media/H300/music/Galactic/We Love 'Em Tonight: Live at Tipitina's" failed: Invalid argument (22)
*** Skipping any contents from this failed directory ***
rsync: mkstemp "/media/H300/music/Dorian/2008 Junior High Camp/.05 - I Walk the Line: The Music of Johnny Cash.ogg.6AsjE0" failed: Invalid argument (22)
rsync: recv_generator: mkdir "/media/H300/music/Seussical: The Musical" failed: Invalid argument (22)
*** Skipping any contents from this failed directory ***
rsync: mkstemp "/media/H300/music/The Mars Volta/Scabdates/.10 - Cicatriz: B. Part II.ogg.i9Ne8u" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mars Volta/Scabdates/.11 - Cicatriz: C. Part III.ogg.mfej2Z" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mars Volta/Scabdates/.12 - Cicatriz: D. Part IV.ogg.T1hOkv" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mars Volta/Scabdates/.3 - Take the Veil Cerpin Taxt: A. Gust of Mutts.ogg.eXUY21" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mars Volta/Scabdates/.4 - Take the Veil Cerpin Taxt: B. And Ghosted Pouts.ogg.KrMaXy" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mars Volta/Scabdates/.9 - Cicatriz: A. Part I.ogg.Ty2Mb6" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mothers of Invention/We're Only in It for the Money/.1 - Are You Hung Up?.ogg.csaAGD" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mothers of Invention/We're Only in It for the Money/.17 - What's the Ugliest Part of Your Body? (reprise).ogg.FDhjjb" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mothers of Invention/We're Only in It for the Money/.2 - Who Needs the Peace Corps?.ogg.SzbV1I" failed: Invalid argument (22)
rsync: mkstemp "/media/H300/music/The Mothers of Invention/We're Only in It for the Money/.8 - What's the Ugliest Part of Your Body?.ogg.dbf1Zg" failed: Invalid argument (22)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]


I'm not sure whats so different about these few songs than the rest of my 4 gig collection.  Anybody know how to fix this?

Thanks.

---

### Post by jonobr on 2009-06-07
hello

Is it always the same files?

Did you try renaming one of those files (if its always the same ones) to something like test.ogg

I have seen it where the target of the copy doesnt lioke certain characters of the file being copied.

---

### Post by codeking on 2009-06-07
Aha, that was it.  Apparently rSync doesn't like colons or question marks.

---

### Post by jonobr on 2009-06-07
super,

just means a bunch of renaming for you:-)

---

### Post by molleradura on 2010-07-21
rsync does all well.
You are writing in a NTFS partition. It is not posible to use ":" in NTFS. (yeah, that sucks a litle ;-) )

---

### Post by NE Key on 2010-11-30
Thank you for that.

I am using Lucky Backup and was it giving errors when copying some of the files in evolution (the mail program) because of the colon in some file names.

Changing the format of the backup medium to a "linux" format solved the problem.

---

