---
title: "Need to list files sorted by size"
date: 2008-08-11
forum: Desktop Environments
---

### Post by ptaramelli on 2008-08-11
Hello!, I have a directory with music, the subdirectories are the artist and some of them have Subsubdirectories (albums), others have files (songs).

I want to list the subdirectories (artists)  by size but when I do that the order is for numbers of elements in it, not size. For example a subdirectory with 50 songs (about said 150 MB) goes before one with 2 subdirectories whose size is said 500 mb.(inverse order of course, that I need) 

How can I do that? , do I have to change nautilus for another file browser? (and in this case wich one?)

Thanks for the answer.

I won't mind if somebody can do that with a script or a little program, I just need to do that once.

---

### Post by ichimunki on 2008-08-12
This can be done from a command prompt (Accessories > Terminal).

```

du --max-depth=1 /path/to/directory | sort -nr

```

will show you a list of all files and subdirectories for '/path/to/directory' in order by size (biggest first).

---

### Post by ptaramelli on 2008-08-28
Thank you, sorry not responding before, I didn t put to get answer by mail

---

