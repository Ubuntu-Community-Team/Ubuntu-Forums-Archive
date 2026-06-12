---
title: "Find where link file leads to"
date: 2009-03-20
forum: General Help
---

### Post by LieToPurify3 on 2009-03-20
I have a file that says its a "link to svg file".  How can I find where the parent file is so I can edit it?

---

### Post by fieroboom on 2009-03-20
Could you be a little more specific? Are you seeing this information in Nautilus? If it's a symlink, then you can open a terminal, cd to the folder with the file, and then run:
```
ls -al
```
That will show you where the symlink points to.
If I'm way off, I'm sorry, but I'm not 100% sure what you're looking at yet.
:D
-Paul

---

