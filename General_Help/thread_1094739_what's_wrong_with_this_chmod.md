---
title: "what's wrong with this chmod?"
date: 2009-03-12
forum: General Help
---

### Post by UranUtan on 2009-03-12
Hi,

I am owner of the /MyFolder1 (this is a 300 GB ext3 partition). When I do ```
chmod -R 644 /MyFolder1/*
``` 

Then all files become inaccessible (nautilus doesn't see anything). ls -l show the left column with plenty of question marks. What I want to do is give me RW and all others R only.

Did I do anything wrong?

---

### Post by shazbut on 2009-03-12
Are you the owner of the files therein?  If so, then I'm not sure why it didn't work.  What does ls -l show?

---

### Post by Defrector on 2009-03-12
When you su to root, can you see the files in ls? Could check who owns em too, might be a clue.

---

### Post by taurus on 2009-03-12
If you want to change, cd,  to /MyFolder1 directory, it needs the executable permission as well.  Therefore, you should do

```
sudo chmod 744 /MyFolder1
ls -la /MyFolder1
```

---

### Post by amauk on 2009-03-12
files set to 644 will be read/write for owner, read for everyone else

directories need to have the execute flag set for anyone needing to navigate into the directory

```
find /MyFolder1 -type d -exec chmod 755 {} \;
find /MyFolder1 -type f -exec chmod 644 {} \;
```

---

### Post by UranUtan on 2009-03-12
> **amauk said:**
> files set to 644 will be read/write for owner, read for everyone else

directories need to have the execute flag set for anyone needing to navigate into the directory

```
find /MyFolder1 -type d -exec chmod 755 {} \;
find /MyFolder1 -type f -exec chmod 644 {} \;
```

This find command you gave is powerful. It does exactly what I wanted.
I need to bookmark this page as there is no way I can remember this syntax.

Thank you very much for your help.

---

### Post by amauk on 2009-03-12
no probs :)

find is powerful
take a look at the man page for it
```
man find
```

you can filter based on any attribute and do a whole heap of operations to matching entries

find & grep are your friends :D
match things based on what they are (find), and what they contain (grep)

---

