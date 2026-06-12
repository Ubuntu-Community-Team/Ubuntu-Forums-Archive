---
title: "Can you provide a little script to move files?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by André on 2006-09-17
Hi everybody,

i am looking for a script to move some files.

I have about 3000 files in a directory with several subdirectories. Now i am looking for a nice command to move them all in the parent directory (like moving all files in the subdirectories of /documents to /documents).

Any idea how to do that?

Greetings
André

---

### Post by mitch.c on 2006-09-17
> **André said:**
> i am looking for a script to move some files.

I have about 3000 files in a directory with several subdirectories. Now i am looking for a nice command to move them all in the parent directory (like moving all files in the subdirectories of /documents to /documents).

Any idea how to do that?

How about:
```
find /path/to/documents -name "*" -type f | xargs mv -f --target-directory\=/path/to/documents 2>/dev/null
```

---

### Post by André on 2006-09-17
Hi mitch.c,

thanks for your post. It is nearly right.

The Output from find contains spaces in the names which makes one file more than one argument.

To cope with the problem i added the following:

```

find /path/to/document -name "*" -type f -print0 | xargs -0 mv --target-directory\=/path/to/document

```

Makes the find output 0 - terminated and tells xargs to expect that, if i got it right...

I like to see the output so i skipped the /dev/null stuff and i want to see if he overwrites somethink kicking -f.

Thanks again.
André

---

### Post by mitch.c on 2006-09-17
> **André said:**
> The Output from find contains spaces in the names which makes one file more than one argument.

To cope with the problem i added the following:

```

find /path/to/document -name "*" -type f -print0 | xargs -0 mv --target-directory\=/path/to/document

```

Makes the find output 0 - terminated and tells xargs to expect that, if i got it right...

Good call! I threw it together pretty quickly when I saw your post this morning. Should have been more careful!

---

