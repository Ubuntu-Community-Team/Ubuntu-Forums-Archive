---
title: "find a folder that contains file1.txt &amp; file2.txt"
date: 2009-06-20
forum: General Help
---

### Post by PGScooter on 2009-06-20
Hi, how can I find a folder that contains a set of files, e.g file1.txt file2.txt file3.txt and directory1
?

these are all very common names and I have a thousand of them individually all over the place, but I want to find the few directories that have them all within them (at the same level... that is: folderiwanttofind/file1.txt folderiwanttofind/directory1 )

Thanks

---

### Post by lloyd_b on 2009-06-20
> **PGScooter said:**
> Hi, how can I find a folder that contains a set of files, e.g file1.txt file2.txt file3.txt and directory1
?

these are all very common names and I have a thousand of them individually all over the place, but I want to find the few directories that have them all within them (at the same level... that is: folderiwanttofind/file1.txt folderiwanttofind/directory1 )

Thanks

A fairly simple shell script will do it:```
#!/bin/bash

CURDIR=$PWD

for DIR in `find . -type d -print`; do
    cd $DIR
    if [ -f file1.txt ] && [ -f file2.txt ] && [ -f file3.txt ] && [ -d directory1 ]; then
        echo "Files found in $DIR"
    fi
    cd $CURDIR
done
```
(Note that this searches in the current directory and below - if the directory you want is outside of that, this script won't find it).

You'll need to customize the "if ..." line for the actual files/directories.  "[ -f file.txt ]" to search for a regular file, "[ -d directory ]" to search for a directory.  Note that the spaces in that statement are *required* - "[-f file.txt]" will NOT work...

This could potentially be improved to where you specify the files/directories to search for on the command line.  Whether that's worth the effort or not depends on how often you plan to use this, and how many different file/directory combinations you expect to have to search for.

Lloyd B.

---

### Post by PGScooter on 2009-06-20
great! that looks like a very intuitive way of doing it. Thank you for the script and for the explanation. I will study and learn from it.

I think I see what you mean with how to improve it.. I would make a command, and then cycle through the arguments (in the ARGV environment variable? or is that just Perl?). I would have to think about how to have the user specify that a given filename is a directory.

thanks!

---

### Post by lloyd_b on 2009-06-20
> **PGScooter said:**
> great! that looks like a very intuitive way of doing it. Thank you for the script and for the explanation. I will study and learn from it.

I think I see what you mean with how to improve it.. I would make a command, and then cycle through the arguments (in the ARGV environment variable? or is that just Perl?). I would have to think about how to have the user specify that a given filename is a directory.

thanks!

In a shell script, the command line arguments are available as $1 (first argument), $2 (second argument), etc, with $# giving you the total number of command line arguments provided.

Note: "man bash" in a terminal window will give you the man page for the bash shell.  It's kinda tough for a beginner to follow at times, but there's TONS of useful info in there.

Lloyd B.

---

### Post by PGScooter on 2009-06-20
great, I'll be sure to check that out.

---

### Post by ghostdog74 on 2009-06-21
well, you can just use find one time and make use of the printf option to print out the files parent directory
```

find . -type f \( -name "file1.txt" -o -name "file2.txt" \) -printf "%h\n"

```

---

