---
title: "Creating MD5 / CRC-32 files for folders?"
date: 2010-07-29
forum: Education &amp; Science
---

### Post by Metal Madness on 2010-07-29
I want to make checksums for my Music and Backup folders, but I can't find a tool for it.
I searched via Google, but the only one I found was  md5sum, which just checks single files.
Do you know a useful tool?

Edit: Does the forum have a bug? I posted in General and now its here

---

### Post by Bachstelze on 2010-07-29
Just make a shell script to use md5sum on all files recursively:

```
#!/bin/bash

function md5
{
        for i in $1; do
                if [ -d $i ]; then
                        md5 $i
                else
                        md5sum $i > ~/files.md5sum
                fi
        done
}

md5 .


```

---

### Post by lloyd_b on 2010-07-29
> **Metal Madness said:**
> I want to make checksums for my Music and Backup folders, but I can't find a tool for it.
I searched via Google, but the only one I found was  md5sum, which just checks single files.
Do you know a useful tool?

Edit: Does the forum have a bug? I posted in General and now its here

The "Unix Philosophy" - build small tools that do one thing, and do it well, and then connect them together to accomplish larger tasks.

Application to your question: "tar -c directory | md5sum".  This will generate a "virtual" archive of the files in "directory", but instead of writing it to disk, it's passed instead to the md5sum program.  Note that you might want to use "-cv" instead of just "-c" so you can see the names of the files it's processing.  Also note that by default 'tar' will process any and all subdirectories under "directory", unless you tell it not to.

Lloyd B.

---

### Post by Metal Madness on 2010-07-29
@ [Bachstelze]("http://ubuntuforums.org/member.php?u=51114")
@ [lloyd_b]("http://ubuntuforums.org/member.php?u=181262")
BIG THANKS ^^

---

