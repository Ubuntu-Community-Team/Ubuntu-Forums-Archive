---
title: "Is there away to batch rename a doc file depending on the title of document"
date: 2018-10-14
forum: Desktop Environments
---

### Post by rizos on 2018-10-14
i need to rename 250 doc files with different file names each one of them (word documents) , and need to be able to rename all files according to the title of the document.
is there a way to do this?

---

### Post by TheFu on 2018-10-14
Can you get the title out through some program?
[https://stackoverflow.com/questions/5671988/how-to-extract-just-plain-text-from-doc-docx-files-unix](https://stackoverflow.com/questions/5671988/how-to-extract-just-plain-text-from-doc-docx-files-unix) has some options.  

If you can, then you could use that solution to make a script that looks something like this:
```

mv filename-1.doc  "title of the doc-filename-1.doc"
mv filename-250.doc  "title of the doc-filename-250.doc"
```

Might want to check if the new filename exists before renaming.

Basically, you'd script something to make a rename script.

---

