---
title: "&quot;Glass&quot; filesystem overlay"
date: 2009-02-13
forum: General Help
---

### Post by Xyem on 2009-02-13
Okay, I don't really know how to explain this one. Please bear with me.

I have a bunch of files which must remain just as they are ( data, location and name-wise ) but would like to be able to access these files from another directory where they will be in a different structure with different names.

Up to here, I could just use hard-links but there is an extra component. I wish to be able to modify the files without affecting the originals. This lead me to look for a COW file-system but copying the entire file isn't what I want it to do either as they can be pretty big. So I started thinking about block-level COW.. which isn't what it is at all.

What I am looking for is the ability to create something like a hard-link but where the changes get written elsewhere. A "glass layer hard-link" if you will.

Does such a thing exist already?

---

