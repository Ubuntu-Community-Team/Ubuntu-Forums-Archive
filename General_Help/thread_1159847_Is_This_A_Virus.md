---
title: "Is This A Virus?"
date: 2009-05-15
forum: General Help
---

### Post by Mark76 on 2009-05-15
According to ClamAV is it.

---

### Post by dcstar on 2009-05-15
> **Mark76 said:**
> According to ClamAV is it.

Something with only 2 bytes in it is nothing at all, let alone a "Virus".

---

### Post by HPD2 on 2009-05-15
many virus scaners look for the word "virus." The file is most likely nothing.

---

### Post by MysticalRiotCandy on 2009-05-15
Here's what I see of the file in a hex editor:
2F 2A
In Base2, it's 0010 1111 : 0010 1010

That's what the file displays: /*.  That's the 2 bytes that are needed to create the two characters.  Nothing else.  You're fine.



Maybe you're confused, and ClamAV has scanned /*, meaning everything inside of the filesystem, and has found one thing to be a virus-infected file.

---

### Post by Mark76 on 2009-05-15
It was bigger when I first opened it in Edit.

Perhaps quarantining it deleted most of the text.

---

