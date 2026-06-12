---
title: "Script to list packages that might be safe to remove"
date: 2006-07-21
forum: Desktop Environments
---

### Post by krismatth3 on 2006-07-21
This script will list installed packages upon which no other packages are dependent (e.g. it will list candidates for deinstallation). However, just because it lists a given package as un-needed DOES NOT MEAN that it's nessecarily safe to remove that package. Use your own judgement!

If you're not sure what a package does, you can use "dpkg -s <pkgname>" to get more information. If you're not certain it's safe to remove a package, DO NOT REMOVE IT. Ask someone!

```

#!/bin/sh

PKGLIST=/tmp/pkglist
DEPLIST=/tmp/deplist

# list packages - trimming top six lines
dpkg -l | grep "^ii" | awk  '{print $2}' > $PKGLIST
NC="`wc -l $PKGLIST | awk '{print $1}'`"

# generate depdency list
rm -f $DEPLIST
I=1
for PKG in `cat /tmp/pkglist`; do
    # write to stderr to allow redirection of unused package list
    dpkg -s $PKG | grep Depends:  >> $DEPLIST
    echo -e -n "Generating depedency list: $I/$NC\r" >&2
    I=`perl -e "print $I+1"`
done

# new line
echo >&2

# list non-dependent files
UNDEPLIST=""
I=1
for PKG in `cat /tmp/pkglist`; do
    # write to stderr to allow redirection of unused package list
    grep $PKG $DEPLIST 2>&1 > /dev/null
    if [ $? -ne 0 ]; then
	UNDEPLIST="$UNDEPLIST $PKG"
    fi
    echo -e -n "Checking packages: $I/$NC\r" >&2
    I=`perl -e "print $I+1"`
done

# output
echo $UNDEPLIST


# cleanup
echo >&2
rm -f $PKGLIST $DEPLIST

```

Improvements, ideas, suggestions? Please post! Please note that you can redirect the output of this file to keep a list around - e.g. "./script.sh > maybe_remove_files.txt".

---

### Post by reacocard on 2006-07-21
take a look at deborphan. does the same thing, and integrates into synaptic too.

---

### Post by aysiu on 2006-07-21
Take a look at *gtkorphan*--it's a graphical frontend for *deborphan*.

---

