---
title: "configurable disk compare process?"
date: 2008-12-23
forum: General Help
---

### Post by maclenin on 2008-12-23
Is there a way to compare two drives/folders/etc (via the terminal) and have the output of that compare process be a user-defined exception log?

For example:

1. I copy drive A to drive B...

2. I configure a separate "process" to output any exceptions (e.g. files present on A which are not present on B)...

3. I run the "process" to compare drive A to B or B to A...

4. Sample output...

```
Exceptions:

~/docs/abc.txt
~/tunes/xyz.mp3
~/pics/mno.jpg
```

...Thanks.

---

### Post by dcstar on 2008-12-23
> **maclenin said:**
> Is there a way to compare two drives/folders/etc (via the terminal) and have the output of that compare process be a user-defined exception log?

For example:

1. I copy drive A to drive B...

2. I configure a separate "process" to output any exceptions (e.g. files present on A which are not present on B)...

3. I run the "process" to compare drive A to B or B to A...

4. Sample output...

```
Exceptions:

~/docs/abc.txt
~/tunes/xyz.mp3
~/pics/mno.jpg
```

...Thanks.

```
man diff
```

---

### Post by maclenin on 2008-12-27
**dcstar**:

Thanks for the **diff** suggestion.

While giving it a whirl using the following syntax...

```
diff ~/dirA/* /media/My\ Passport/dirA/*
```

...to compare the contents of two directories (dirA) - on two separate drives - using a wild card (*) to try and compare not only the parent directories (dirA) but also all of their children (*) and grandchildren (*) and associated files (*), I received the following error...

```
diff: extra operand `/home/dirA/dirX'
```

With a little googling I came across this possible [_explanation_]("http://zotline.com/shownote.zot/NoteNum/3001.html") of the error, which would lead me to believe that **diff** can only be used to compare the contents of two files or of two directories and their contents (i.e. immediate subdirectories and files in a parent directory - seems strange/limited to me)...

...any thoughts?

---

### Post by maclenin on 2008-12-27
**dcstar**: 

```
diff -r
```

...thanks for leading me down the right path.

...might **rsync** or some such be a more efficient way of archiving and copying and comparing (multiple gigs of data and files)?

...thanks, again, for the **diff** lead.

---

