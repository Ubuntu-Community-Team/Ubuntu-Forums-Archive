---
title: "How to remove a specific line via a shellscript?"
date: 2009-06-23
forum: General Help
---

### Post by Hetor on 2009-06-23
I need a way to remove a line with specific text from a text file. For example, to remove a repository from /etc/apt/sources.list. I heared sed can delete lines, but I don't understand the syntax. Please help me.

---

### Post by Celauran on 2009-06-23
```
sed -i '/pattern/d' filename
```

Will remove any line in 'filename' that contains 'pattern'.

---

### Post by Hetor on 2009-06-23
Thank you, I will try that :)

EDIT: Works! :D Awesome.

---

