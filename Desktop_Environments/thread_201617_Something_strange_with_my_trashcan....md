---
title: "Something strange with my trashcan..."
date: 2006-06-22
forum: Desktop Environments
---

### Post by 3zrael on 2006-06-22
Hello!
Last evening I was considering the size of my /home directory, thinking it was really too big for the objects it contained. So I looked for the reason for such a big occupation on my hdd... 

I discovered that  ~./local/share/Trash was 2.4GB... This is the trashcan directory, it has two different directory in it: /files and /docs.
One holds the deleted files , the other one some text files with the name and something else about the deleted files.

There were 2.4GB in /file and NOTHING in /docs... WHY??? how it could be possible? I deleted everything in /files... did I make something wrong?

:confused:

---

### Post by 3zrael on 2006-06-22
...please..:(

---

### Post by 3zrael on 2006-06-23
sigh...

---

### Post by aysiu on 2006-06-23
I'm not understanding what the issue is.

---

### Post by 3zrael on 2006-06-23
Hello!
The issue is that I found 2.4GB files in the trashcan dir and I were unable to delete them using the "ktrash --empty" command because there were no text files in the /info directory...  I had to clean ~./local/share/Trash/files manually.
My question is: what could be happened to my trashcan? Now it works well... there was a bug in the past or something like that???

---

