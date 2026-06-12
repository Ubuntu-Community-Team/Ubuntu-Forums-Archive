---
title: "How do I clone (&quot;ghost&quot;) a hard-disk?"
date: 2009-02-10
forum: General Help
---

### Post by blueturtl on 2009-02-10
I have a dual booting system with an aging hard-disk and I was wondering if I could clone it's contents to my Linux file system for backup purposes.

An obvious way would simply be to use tar to create an archive file that would contain everything on the target drive, but I don't know if tar would record all the essential system files.

The reason I want to do this is that restoring the image would be so much quicker and easier than actually having to reinstall Windows and all the programs I use with it.

Does anyone have ideas better than tar?

---

### Post by taurus on 2009-02-10
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Slim Odds on 2009-02-10
+1 Clonezilla

---

### Post by blueturtl on 2009-02-10
Wow. I had no idea such a mature tool was available for this task. I will look in to it. Meanwhile I'm still welcoming other suggestions for the sake of learning.

---

### Post by blueturtl on 2009-02-11
(Bump) No command line voodoo you could do with a base install?
Anyone?

---

### Post by Graham1 on 2009-03-07
Other cloning solutions available are G4L (Ghost for Linux) and PING (Partimage Is Not Ghost). 

My favourite is G4L although from my tests, Clonezilla was the clear favourite (in speed) when backing up but not so hot when restoring (G4L and PING were faster). 

Use PartImage for Linux partitions (in your case) and NTFSClone for Windows. Have fun. 

:)

---

