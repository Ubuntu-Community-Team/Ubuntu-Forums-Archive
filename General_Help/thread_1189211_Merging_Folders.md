---
title: "Merging Folders"
date: 2009-06-16
forum: General Help
---

### Post by monsieurdozier on 2009-06-16
I'm wanting to merge different folders on my harddrive.

They're listed as:

01.01
01.02
01.03
01.04
02.01
02.02
02.03
02.04
02.05
etc...

I was hoping for an automated way to merge all the 01.0X folders together, 02.0X folders, etc.

They all contain different content, and have no subdirectories.

What can I use to merge them?

-Monsieur Dozier

---

### Post by pytheas22 on 2009-06-16
If all you want to do is combine all the contents of the 1.0X folders into a single directory, and combine all the 2.0X into another, etc., then you could simply use the cp command with a wildcard.  For example:
```

cp 1.0*/* /path/to/new/1.0/folder
```

This will leave the original files in place, since it's copying rather than moving them.  You'd have to go back and delete the original files when it's done.

---

### Post by monsieurdozier on 2009-06-16
This will work for what I need it for.

Thanks Much

Monsieur Dozier

---

