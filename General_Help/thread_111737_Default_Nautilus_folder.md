---
title: "Default Nautilus folder"
date: 2006-01-02
forum: General Help
---

### Post by martibs on 2006-01-02
How can I set which folder Nautilus should show when I start it?

---

### Post by bjourne on 2006-01-07
You pass the folder as a command line argument to natutilus:

$ nautilus /name/of/folder

---

### Post by magnusbb on 2006-01-07
Yes, as martibs says, you can pass the the folder as a command argument to Nautilus. But, to answer your question more directly, you can do it by fx. creating an alias in your default shell.

Open the file .bashrc (located in your home folder) in your favourite text editor and type:

```
alias nautilus="nautilus /path/to/folder"
```

When you type nautilus in a Terminal, it should open your favourite folder.

---

