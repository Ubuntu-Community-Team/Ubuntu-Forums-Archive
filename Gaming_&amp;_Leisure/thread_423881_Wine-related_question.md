---
title: "Wine-related question"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by topsites on 2007-04-26
Ok, I am running Ubuntu Dapper 6.06 LTS (and only that, no Windows).
It says in some instructions i need to add certain files to the C:\...\Windows folder
and I know this folder exists somewhere within wine as its part of the setup but for the life of me I can not find it...
Anyone know where Wine's Windows emu folder is, where it keeps essential emu files?

---

### Post by leg on 2007-04-26
Inside the .wine directory. The dot makes it a hidden directory on Linux so you will need to show hidden files to see it or ```
cd ~/.wine
ls 
``` from a terminal.

---

### Post by AndrewRiedi on 2007-04-26
```
cd ~/.wine/drive_c/windows
```

---

### Post by cogadh on 2007-04-26
If you don't like the terminal, just open up the file browser in your home directory and press CTRL-H, that will temporarily display all the hidden files and folders for you.

---

