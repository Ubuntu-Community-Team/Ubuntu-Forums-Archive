---
title: "Assistance required"
date: 2009-03-23
forum: General Help
---

### Post by N00bSupreme on 2009-03-23
I need some help creating a script to copy files in a directory to another directory of my choosing (ie copy /etc) and if the directory doesnt exist i need the option to create it

Any help is greatly appreciated

Thanks

---

### Post by James_Lochhead on 2009-03-23
Am no expert but:
echo "Enter a source directory (absolute):" 
read DIRPATH1
echo "Enter a target directory (absolute):"
read DIRPATH2
mkdir $DIRPATH2
cp $DIRPATH1/* $DIRPATH2

---

### Post by mb_webguy on 2009-03-23
What's wrong with the cp command?  It will create the destination if it doesn't exist.  Use the "-R" option to recursively copy the contents of a directory.

---

### Post by James_Lochhead on 2009-03-23
Yea it works. Just make sure that you are only copying inside your home directory and that you do not make the target inside the original folder (folder will be copied in to itself - breaking script).

---

### Post by James_Lochhead on 2009-03-23
> **mb_webguy said:**
> What's wrong with the cp command?  It will create the destination if it doesn't exist.  Use the "-R" option to recursively copy the contents of a directory.

#!/bin/bash
echo "Enter a source directory:"
read DIRPATH1
echo "Enter a target directory:"
read DIRPATH2
cp -R $DIRPATH1/* $DIRPATH2

There we go.

---

