---
title: "Find (and delete) any file that is not type x"
date: 2009-04-10
forum: General Help
---

### Post by GabrielWolff on 2009-04-10
I have a directory with about a 1000 sub-directories.
I want to list all the files that are not of type .xxx (in this case: .mp3) and eventually delete them [but have a look at them first, so I need the search-only option].

I had a look at the man pages of find and locate, but unsuccessfully.

Any ideas?

---

### Post by smcleish on 2009-04-10
The commands assume your current directory is the one containing all the subdirectories.

To list the files, try

% find . -depth -name "*.xxx" > listing.txt

That will list them in the file listing.txt so you can check through the list at your leisure. More options may be needed if some of the subdirectories contain symbolic links.

To delete the files, try

% find . -name "*.xxx" -delete

That should delete exactly the same files as listed by the previous command. You want to be absolutely sure that you have the right set of files from the previous command before you run this!

Cheers,
Simon

---

### Post by GabrielWolff on 2009-04-10
> **smcleish said:**
> The commands assume your current directory is the one containing all the subdirectories.

To list the files, try

% find . -depth -name "*.xxx" > listing.txt

That will list them in the file listing.txt so you can check through the list at your leisure. More options may be needed if some of the subdirectories contain symbolic links.

To delete the files, try

% find . -name "*.xxx" -delete

That should delete exactly the same files as listed by the previous command. You want to be absolutely sure that you have the right set of files from the previous command before you run this!

Cheers,
Simon

Thanks. But this will give me a result that includes any files of the type xxx, while I want to have a list of all the files of any type *other than xxx*. Is that possible?

---

### Post by darthmob on 2009-04-10
there is nothing you can not do with simple shellscripts when it comes to those things!

if you just want to view special files I would suggest *ls* ([click for manpage]("http://www.linuxmanpages.com/man1/ls.1.php")).

one simple example:
```
ls -R --ignore=*.mp3 /home/GabrielWolff
```would return all files in your homefolder and subfolders (-R) except mp3 files (--ignore=*.mp3; the * matches everything or nothing and the .mp3 only .mp3). have a look at the man page for more viewing options.

---

### Post by smcleish on 2009-04-10
> **GabrielWolff said:**
> Thanks. But this will give me a result that includes any files of the type xxx, while I want to have a list of all the files of any type *other than xxx*. Is that possible?

Sorry, misread your requirement.

A possible find syntax for what you want is:

find . -depth \! \( -name "*.xxx" -o -type "d" \)

assuming you don't want all the directories included in the listing.

Cheers,
Simon

---

