---
title: "Quick scripting question"
date: 2009-05-19
forum: General Help
---

### Post by blazemore on 2009-05-19
I want to write a program that moniters a folder, and when a .flv file is detected, it converts it to mpeg with ffmpeg, copies it to a folder, and deletes the original.

How can I do it?
(I'll modify the script, it's just the monitoring thing that I don't know how to do)

---

### Post by cdenley on 2009-05-19
> **blazemore said:**
> I want to write a program that moniters a folder, and when a .flv file is detected, it converts it to mpeg with ffmpeg, copies it to a folder, and deletes the original.

How can I do it?
(I'll modify the script, it's just the monitoring thing that I don't know how to do)

You mean something like this?
```

#!/bin/sh
IFS="
"
for FILE in `ls -1 /path/to/dir/*.flv`; do
convert $FILE
done

```

---

### Post by StOoZ on 2009-05-19
I think he meant that he wants to constantly monitor the directory , the current for loop will end when all files are scanned , what about if  there are no files?? we need to wait for files...
so a form of
while true
do
.
.
done

form would fit better I believe.

---

### Post by cdenley on 2009-05-19
> **StOoZ said:**
> I think he meant that he wants to constantly monitor the directory , the current for loop will end when all files are scanned , what about if  there are no files?? we need to wait for files...
so a form of
while true
do
.
.
done

form would fit better I believe.

I would just schedule a cron job to run as frequently as needed, rather than have a script running indefinitely. If you do use an infinite loop, make sure you use sleep, because you don't want to list a directory 20 times a second until a new file appears.

---

### Post by prem1er on 2009-05-19
What language? I'm am currently writing the same task in python.  Let me know if you want me to show you how I am doing it.  Python has a nice module written to monitor a directory.  When if finds a change in the directory it will return the new file that has been added.  Then you can do whatever you want with the new folder.

---

### Post by blazemore on 2009-05-19
YES Python would be perfect! Please show me your progress. What I'm looking for is something like this (pseudocode):
```
while true:
if a file is created in /foo/bar
run ffmpeg -i /foo/bar/file.flv -o /foo/bar/file.mpeg
rm -fv /foo/bar/file.flv
cp /foo/bar/file.mpeg /media/iPod

```

Problem with this:
The script registers that there's an flv file there, even though ffmpeg is already converting it. This would cause hundreds if not thousands of conversions at the same time.

---

### Post by cdenley on 2009-05-19
> **blazemore said:**
> YES Python would be perfect! Please show me your progress. What I'm looking for is something like this (pseudocode):
```
while true:
if a file is created in /foo/bar
run ffmpeg -i /foo/bar/file.flv -o /foo/bar/file.mpeg
rm -fv /foo/bar/file.flv
cp /foo/bar/file.mpeg /media/iPod

```

Problem with this:
The script registers that there's an flv file there, even though ffmpeg is already converting it. This would cause hundreds if not thousands of conversions at the same time.

```

#!/bin/sh
IFS="
"
while [ 1 ]; do
LIST=`ls -1 /foo/bar/*.flv`
if [ $? -eq 0 ]; then
for FILE in $LIST; do
TEMP="$FILE~"
DEST="$FILE.mpeg"
mv $FILE $TEMP
ffmpeg -i $TEMP -o $DEST
rm -fv $TEMP
cp $DEST /media/iPod
done
fi
sleep 10
done

```

---

### Post by SentientFluid on 2009-05-19
> **cdenley said:**
> ```

#!/bin/sh
IFS="
"
```

For IFS is that a space and then a new line or just a new line?

---

### Post by spillin_dylan on 2009-05-19
It looks like it's just a newline.  

But, possibly more importantly, what does ```
IFS="
"
``` actually DO?

---

### Post by geirha on 2009-05-20
IFS (Internal field separator) is initially set to <space><tab><new-line>. It tells the for loop what characters to use as delimiters. In the case above, it's probably intended to stop spaces in filenames to be treated as delimiters, rather than part of the filename.

```
man bash   # And search for IFS
```

The script will unfortunately fail later on though, on files with spaces. In general one should avoid looping through the output of ls and instead rely on the shells pathname expansion, and also, always "quote" variables containing pathnames.

Here's a script based on cdenley's idea, that should handle filenames with spaces (and even newlines) in them. Instead of renaming the file it's working on, it moves it to an "in_progress" directory.
```

#!/bin/bash
srcdir="/place/where/flvs/pop/up"
destdir="/place/to/put/mpegs"
workdir="$srcdir/in_progress"

[ -d "$workdir" ] || mkdir "$workdir"   # Create $workdir if it doesn't exist
while true; do
  for file in "$srcdir"/*.flv; do
    base=$(basename "$file")      # Get filename without the directory components
    mpgfile="${base/%.flv/.mpg}"  # Replace .flv with .mpg

    mv "$file" "$workdir" &&
    ffmpeg -i "$workdir/$base" -o "$workdir/$mpgfile" &&
    mv "$workdir/$mpgfile" "$destdir" &&
    rm -f "$workdir/$base"
  done
  sleep 10
done
```

It should work as long as only one instance of the script is running at a time.

---

