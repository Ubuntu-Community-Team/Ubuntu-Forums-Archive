---
title: "Making rm alias/script"
date: 2009-01-08
forum: General Help
---

### Post by Buce on 2009-01-08
First-time poster here.

I want to make it so that invoking "rm" from the command line will move the file to the trash if it resides on my computer, and completely remove the file if it's on a usb flash drive or some other external media.

So basically, I want to make an alias or write a script for ~/bin that will do a ```
mv -t ~/.local/share/Trash/files --backup=t [file]
``` if [file] is on sda; otherwise: ```
rm -i [file]
```

Is there a way to use fdisk to determine which drive a file is on? Or am I approaching this from the wrong direction? I'm a bit of a beginner with linux, so any help would be much appreciated.

---

### Post by aloshbennett on 2009-01-08
you could use 'df .' to figure out what device is mounted as the current folder.

cheers!

---

### Post by mezhaka on 2009-02-23
I'd really would like to know how to do that. Please share if you've found the way.

---

### Post by heindsight on 2009-02-23
I've written a small script to do something like this.

It takes a list of filenames and for each file:
[LIST]
[*]if it is located under your home directory (and on the same device as your home directory), it is moved to ~/.local/share/Trash/files
[*]Otherwise, if it is located on a device listed in /etc/fstab the file is moved to MOUNTPOINT/.Trash-UID/files (where MOUNTPOINT is the mountpoint of the filesystem and UID is your numeric user id)
[*]Otherwise it is deleted using rm
[/LIST]

In the cases where the file is moved to a Trash directory, an entry is also created in the corresponding Trash/info directory.

EDIT:
I've removed this script, further down this thread I posted a much better way to achieve this sort of thing.

---

### Post by lloyd_b on 2009-02-23
> **Buce said:**
> First-time poster here.

I want to make it so that invoking "rm" from the command line will move the file to the trash if it resides on my computer, and completely remove the file if it's on a usb flash drive or some other external media.

So basically, I want to make an alias or write a script for ~/bin that will do a ```
mv -t ~/.local/share/Trash/files --backup=t [file]
``` if [file] is on sda; otherwise: ```
rm -i [file]
```

Is there a way to use fdisk to determine which drive a file is on? Or am I approaching this from the wrong direction? I'm a bit of a beginner with linux, so any help would be much appreciated.

I *think* you can make use of the "filesystem ID" returned by the "stat" command to determine which *filesystem* the file is on, and then execute either a "mv" or real "rm" based on that.

Here's a sample script, using the filesystem ID's on my system - you'll have to use "stat" to get the proper ID's for your machine...
[PHP]#!/bin/bash

# saferm
#
# A wrapper for the "rm" command, which will determine the filesystem, and move the file to
# a specified "trash" area if the filesystem is listed.  Otherwise, the file will actually
# be deleted.
#
# Usage: saferm [filename]
#
# Note: Does *not* attempt to handle the various options of the real "rm" command!

if [ -z $1 ]; then
    echo "Usage: saferm [filename]"
    exit 0
fi

FILESYSTEM=`stat -f -c "%i" $1`

# If "stat" hit an error, FILESYSTEM will be null 
if [ -z $FILESYSTEM ]; then
    echo "Unable to stat $1"
    exit 0
fi

# Test FILESYSTEM against my filesystems.  In my case, there are two on the
# drive - "/" and "/home".  Move them to the "mytrash" subdirectory on that
# filesystem (by having a separate "mytrash" on each filesystem, the "mv"
# command is very fast.  If I tried to use a global "mytrash", a "mv" from
# a different filesystem would actually execute a "copy and delete", which
# can be very slow for large files).

if [ "$FILESYSTEM" == "f7047fb703ff8f90" ]; then
    # "/" filesystem
    mv -t /mytrash --backup=t $1
elif [ "$FILESYSTEM" == "81ad851bb895197" ]; then
    # "/home" filesystem
    mv -t /home/mytrash --backup=t $1
else
    # Somewhere else - delete it
    rm -i $1
fi[/PHP]
Note that this is pretty simplistic.  It could easily be extended to handle multiple files on the command line with a simple "for" loop, but I just wanted to show the basic concept.

Lloyd B.

---

### Post by sisco311 on 2009-02-23
why reinvent the wheel?

```
gvfs-trash /path/to/file
```
;)

---

### Post by heindsight on 2009-02-23
> **sisco311 said:**
> why reinvent the wheel?

```
gvfs-trash /path/to/file
```
;)

Aha, I knew there must be a command to do that, just couldn't find it :D

---

### Post by heindsight on 2009-02-23
Here's a much more efficient way to achieve the same thing.

```
#!/bin/sh

SCRIPT=${0##*/}
DEVS=$(stat -c %D $(awk '(!/^[[:blank:]]*#/)&&($2 != "none"){print$2}' /etc/fstab))

for f in "$@"; do
    if [ ! -e "$f" ]; then
        echo >&2 "$SCRIPT: couldn't remove '$f': No such file or directory"
        continue
    fi

    dev=$(stat -c %D "$f")

    if echo $DEVS | grep $dev > /dev/null; then
        gvfs-trash "$f"
    else
        rm $f
    fi
done
```

---

### Post by Buce on 2009-07-14
I never got around to working on this, but it looks like people have come up with a solution, or if not, some good leads at least, so I'm marking this thread solved.

---

