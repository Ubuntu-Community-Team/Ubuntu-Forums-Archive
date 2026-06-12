---
title: "Command line search mp3 by tag"
date: 2009-05-08
forum: General Help
---

### Post by dualE5335 on 2009-05-08
Greetings-
Are there switches to the find command (like -name, -type, -path, -atime, etc) that would allow me to search within mp3 tags from the command line?

Ideally something like 

```
find -type f -mp3tag genre "rock"
``` to find all files with a genre tag of rock

Is there some creative use of grep, or any other CLI friendly app, to do this?

(needs to be CLI based because I'm not running a GUI)

Thanks

---

### Post by lloyd_b on 2009-05-08
> **dualE5335 said:**
> Greetings-
Are there switches to the find command (like -name, -type, -path, -atime, etc) that would allow me to search within mp3 tags from the command line?

Ideally something like 

```
find -type f -mp3tag genre "rock"
``` to find all files with a genre tag of rock

Is there some creative use of grep, or any other CLI friendly app, to do this?

(needs to be CLI based because I'm not running a GUI)

Thanks
First, install the package "mp3info" - this provides the tool to actually pull the tags from the mp3 files.

Here's a command line to actually accomplish what you want:```
find . -name "*.mp3" -exec mp3info -p "%F@%g\n" {} 2>/dev/null  \; | grep "@Rock" | cut -d '@' -f1
```

The "find" you already understand.

The 'mp3info -p "%F@%g"' will output the files in the format "Filename@Genre" (Needed the @ as a separator to pull the Genre off later).

2>/dev/null is because mp3info insists on printing an error message if the file doesn't happen to have any ID3 tags.  Don't know if this'll be a problem for you.

The cut command trims off everything from the @ on, leaving just the filename (with full path)

Note: Because I used @ as the separator, if any of the files happen to have that character in the file name, you'll get garbage.  Just select a different separator...

Lloyd B.

---

