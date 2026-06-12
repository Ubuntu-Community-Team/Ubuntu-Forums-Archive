---
title: "burn iso image without checksum activity?"
date: 2009-06-05
forum: General Help
---

### Post by candtalan on 2009-06-05
I notice in 9.04 that both of the 'burn image' options in the context menu seem to include the activity of automatically checking the burn with a calculated checksum.

Previously, when using the lts 8.04, it was possible to choose brasero (which created its own check) or simply 'Write to disc' (which did no check).

When burning a lot of CD copies, I would expect to maybe do a sample check with a terminal and md5sum, but with 9.04 there does not seem to be a choice of a simple burn, with no check.

Have I missed something? is there another simple way in 9.04 to just burn an iso with burn-proof techniques etc, but not necessarily 'forcing' an md5sum check each time?

Comments appreciated

---

### Post by binbash on 2009-06-05
Did you try to disable file checksum plugin at brasero?

---

### Post by candtalan on 2009-06-05
thanks. 
No, it sounds useful, but how do I do that please?

---

### Post by candtalan on 2009-06-05
Ah! Found it , thanks

---

### Post by jenkinbr on 2009-06-05
That's one reason I don't like brasero -- I've set nautilus-cd-burner as the default for .iso files (I tried disableing the md5check plugin, but it kept re-enabling itself :()

---

