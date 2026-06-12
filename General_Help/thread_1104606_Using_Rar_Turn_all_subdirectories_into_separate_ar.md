---
title: "Using Rar: Turn all subdirectories into separate archives."
date: 2009-03-23
forum: General Help
---

### Post by brownbat on 2009-03-23
Is there an easy way for rar to take all 40 or so directories in a certain folder and turn them into archives with one command?

I did not find an easy way to do this in the manual, perhaps some sort of bash code is required?

---

### Post by Xiong Chiamiov on 2009-03-23
```

#!/bin/sh

for directory in ls; do
  tar czvf $directory
done;

```
My bash is a bit rusty, so I probably got some punctuation wrong there.  Also, that only works if there are no spaces in filenames; if there are, the easiest way I've found is to use Perl instead.

---

### Post by brownbat on 2009-03-24
There are spaces in those directories. Here's what I've discovered so far:

```

#!/bin/sh

for directory in *
do
  echo $directory
done;

```
Lists all the sub-directories in my home folder.

While...
```

#!/bin/sh

for directory in '*'
do
  echo $directory
done;

```
Lists all the same sub-directories but without line breaks.

"for directory in ls" or "for directory in ./" or "for directory in './'" outputs 'ls', './', or './' respectively.

[This site]("http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html") has an example similar to what I need for Java compilation.

I feel I'm getting very close, and will post what I finally use.

UPDATE:
```

#!/bin/sh

for directory in temp/*
do
  rar a $directory.rar $directory
done;

```
works for no spaces. [I feel I should be using a more open archive format than rar, but cbr and cbz are the standard comic formats, so rar or zip is the goal here. On the open source continuum of cognitive dissonance, would "cbz" be considered superior to "cbr"? :)]

UPDATE 2:
```
#!/bin/sh

for directory in temp/*
do
  rar a "$directory.rar" "$directory"
done;
```

Works for spaces. Single quotes do not work, and a discussion of this can be found [here]("http://ubuntuforums.org/archive/index.php/t-434566.html"), found archived in the greatest forums on the Internet.

---

### Post by brownbat on 2009-03-24
This very issue was also discussed [here]("http://ubuntuforums.org/showthread.php?t=557044"), guess my search foo was weak tonight.

---

