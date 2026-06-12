---
title: "categorize files into folders"
date: 2009-06-23
forum: General Help
---

### Post by rosenth on 2009-06-23
hi
I have alot of files in a folder, which are categorized by this name pattern xxxyyy.mp3 ,which xxx means category number and yyy means subcategory number.
i have to seperate them into their folders according to the category number (xxx).
so how is `for loop` bash command for this?

---

### Post by lloyd_b on 2009-06-23
> **rosenth said:**
> hi
I have alot of files in a folder, which are categorized by this name pattern xxxyyy.mp3 ,which xxx means category number and yyy means subcategory number.
i have to seperate them into their folders according to the category number (xxx).
so how is `for loop` bash command for this?

Here's a simple script.  Note that this script assumes that the category subdirectories already exist (it could be modified to create them).
```
#!/bin/bash

# Select all mp3 files in current directory
for FILE in *.mp3; do
    # Extract the category from the first three characters of the filename
    CATEGORY=${FILE:0:3}

    # Copy the current file to the category subdirectory
    cp "$FILE" "$CATEGORY"
done
```

Lloyd B.

---

### Post by rosenth on 2009-06-24
thanx alot!
```
#!/bin/bash



# Select all mp3 files in current directory

for FILE in *.mp3; do

    # Extract the category from the first three characters of the filename

    CATEGORY=${FILE:0:3}



    # Copy the current file to the category subdirectory

    mkdir "$CATEGORY"

    cp "$FILE" "$CATEGORY"

done

```

---

### Post by lloyd_b on 2009-06-24
One issue with just blindly issuing the "mkdir" command - assuming that you have many files falling into each category, you're going to get a lot of error messages, when it tries to create a directory that already exists.

I'd suggest the following:```
if ! [ -d "$CATEGORY" ]; then
    mkdir "$CATEGORY"
fi
```This will check to see if there is already a directory by that name, and only execute the "mkdir" if it doesn't exist. 

Lloyd B.

---

