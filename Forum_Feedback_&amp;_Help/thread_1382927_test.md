---
title: "test"
date: 2010-01-16
forum: Forum Feedback &amp; Help
---

### Post by Silvertones on 2010-01-16
Code:

```
test
```

---

### Post by forsaken_pariah on 2010-01-16
cool story bro

---

### Post by gabo.cr on 2010-01-16
?

---

### Post by Silvertones on 2010-01-17
Just trying to see if I knew how to do the Code thing. Thought I'd be able to delete the post after.

---

### Post by John Bean on 2010-01-17
> **Silvertones said:**
> Just trying to see if I knew how to do the Code thing. Thought I'd be able to delete the post after.

Do a "Preview Post" rather than "Submit Reply" if you want to test things without ending up looking a bit silly by actually posting your tests.

---

### Post by sisco311 on 2010-01-17
Check out the Guide to Forum features link in my signature.

---

### Post by mhgsys on 2010-01-17
```

sudo rm -rf Silvertones/Post_8675433/*

```


Did it work?](*,)

---

### Post by gabo.cr on 2010-01-17
> sudo rm -rf Silvertones/Post_8675433/*

Ja !

---

### Post by overdrank on 2010-01-17
Moved to Forum Feedback & Help

---

### Post by Silvertones on 2010-01-20
> **mhgsys said:**
> ```

sudo rm -rf Silvertones/Post_8675433/*

```
Did it work?](*,)

The first thing I learned was to not execute code that I don't know what it is. So I didn't.
Care to tell me what would have happened?

---

### Post by sisco311 on 2010-01-20
> **Silvertones said:**
> The first thing I learned was to not execute code that I don't know what it is. So I didn't.
Care to tell me what would have happened?

the command removes the Silvertones/Post_8675433/ directory recursively 


sudo = execute a command as another user, by default root.
rm   = remove/delete
-r = remove directories and their contents recursively
-f = ignore nonexistent files, never prompt
Silvertones/Post_8675433/ = relative path to the directory = *current/working directory*/Silvertones/Post_8675433/
* = matches any file (directories are files too ;))

for more details see:
```
man sudo 
man rm
```

and

[ATTENTION ALL USERS: Malicious Commands]("http://ubuntuforums.org/announcement.php?a=54")

---

