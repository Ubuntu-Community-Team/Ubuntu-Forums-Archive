---
title: "command to output a directory tree map"
date: 2009-06-23
forum: General Help
---

### Post by TripleSix on 2009-06-23
I need to make an output of a directory tree with all its files, something like this

```

map
|
+-- submap
|     |
|     +-- file1.ext
|     +-- file2.ext
|     +-- file3.ext
|
+-- submap
|
.

```

Is there a quick way to do something like this?

---

### Post by vikkikanhaua on 2009-06-23
this script will help.{this is not my script}

```
#!/bin/bash
# tree.sh
#  Written by Rick Boivie.
#  Used with permission.
#  This is a revised and simplified version of a script
#+ by Jordi Sanfeliu (and patched by Ian Kjos).
#  This script replaces the earlier version used in
#+ previous releases of the Advanced Bash Scripting Guide.
# ==> Comments added by the author of this document.
search () {
for dir in `echo *`
# ==> `echo *` lists all the files in current working directory,
#+ ==> without line breaks.
# ==> Similar effect to for dir in *
# ==> but "dir in `echo *`" will not handle filenames with blanks.
do
   if [ -d "$dir" ] ; then # ==> If it is a directory (-d)...
   zz=0                     # ==> Temp variable, keeping track of directory level.
   while [ $zz != $1 ]      # Keep track of inner nested loop.
     do
        echo -n "| "        # ==> Display vertical connector symbol,
                            # ==> with 2 spaces & no line feed in order to indent.
        zz=`expr $zz + 1`   # ==> Increment zz.
     done
     if [ -L "$dir" ] ; then # ==> If directory is a symbolic link...
        echo "+---$dir" `ls -l $dir | sed 's/^.*'$dir' //'`
        # ==> Display horiz. connector and list directory name, but...
        # ==> delete date/time part of long listing.
     else
        echo "+---$dir"        # ==> Display horizontal connector symbol...
        # ==> and print directory name.
        numdirs=`expr $numdirs + 1` # ==> Increment directory count.
        if cd "$dir" ; then          # ==> If can move to subdirectory...
          search `expr $1 + 1`       # with recursion ;-)
          # ==> Function calls itself.
          cd ..
        fi
     fi
   fi
done
}
if [ $# != 0 ] ; then
   cd $1 # move to indicated directory.
   #else # stay in current directory
fi
echo "Initial directory = `pwd`"
numdirs=0
search 0
echo "Total directories = $numdirs"
exit 0

```

---

### Post by prshah on 2009-06-23
> **TripleSix said:**
> I need to make an output of a directory tree with all its files, something like this
Is there a quick way to do something like this?

```
sudo apt-get install tree
tree
```

---

