---
title: "Moving files to subdirs based on filename."
date: 2009-05-08
forum: General Help
---

### Post by haired on 2009-05-08
Hi,

My knowledge of bash is rather limited, and I know there is someone here with the know-how to execute the following:

Plan is to move files with the same filename (different extensions) to a subdir. of their current directories named CD1, CD2, CD3 etc.

Thing is, I only want the files to be moved if the total filesize of them is >690MB, also if there is only one filename.ext, leave it as it is.


Note: They should be moved in alphabetical ascending order. ie. CD1: FILE_A.001, CD2: FILE_B.001

Thanks in advanced, and any replies will be much appreciated!

---

### Post by haired on 2009-05-08
Bump, sorry.

---

### Post by milton1 on 2009-05-08
The easiest way to do this is probably with a python script. Python can pass commands to a bash shell. You could use some manner of array or something to read in the files, then use a loop to move them exactly where you want them based on filenames.

I don't recall the exact syntax for handing commands to the command line, but I'm sure a quick search will find them easily.

---

### Post by geirha on 2009-05-08
Not sure I understand what you want to do exactly. A more detailed example of what you want to do would help.

---

### Post by haired on 2009-05-08
Thanks for the replies,

milton, by bash skills I meant everything script/coding based. :D

As for process, here's a screenshot example series of events.

Directory containing files:

[IMG]http://i40.tinypic.com/3480v0x.png[/IMG]

Files containing 'example-file-A' been moved to CD1 and 'example-file-B' to CD2:

[IMG]http://i43.tinypic.com/23u63aw.png[/IMG]

Contents of CD1:

[IMG]http://i40.tinypic.com/1zz16dd.png[/IMG]

Contents of CD2:

[IMG]http://i41.tinypic.com/212cvpd.png[/IMG]


Hopefully this clears it up, and again, most grateful.


Note: If there is only one file filename in the directory the script is being run in, those aren't to be moved to subdirs.

---

### Post by geirha on 2009-05-08
Ok, I think I understand what you want now. Does the following little script do what you want?

```

#!/bin/bash

# sum the size of all regular files in the current directory
total_filesize=0
for file in *; do
    [ -f "$file" ] || continue
    filesize=$(stat -c %s "$file")
    ((total_filesize += filesize))
done

if [ $total_filesize -lt 690000000 ]; then
    echo "Total filesize $total_filesize is less than 690MB. Exiting."
    exit 0
fi


counter=1
# Creates a new CD$counter directory and moves all files given as arguments, 
# if more than 1 argument is passed.
process_files ()
{
    [ $# -gt 1 ] || return 0
    # Find the next available name to name directory (CD1, CD2, CD3 etc.)
    while [ -e "CD$counter" ]; do ((counter++)); done
    mkdir -v "CD$counter"
    mv -v "$@" "CD$counter"
}

# Iterate through all regular files, stripping the extension and moving as
# necessary
for file in *; do
    [ -f "$file" ] || continue
    base=${file%.*}
    process_files "$base".*
done

```

---

### Post by haired on 2009-05-08
Wow, that does seem incredibly promising. I'm in the middle of a distro. upgrade atm. I'll get back to you within an hour to report.


Edit: Yes, that is perfect.:D

Did the trick. Thanks again!

---

