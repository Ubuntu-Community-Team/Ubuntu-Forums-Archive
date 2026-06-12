---
title: "Reading  dot url files in firefox"
date: 2006-10-23
forum: Desktop Environments
---

### Post by Crc-3rr0r on 2006-10-23
Hi how do get firefox to recognise url files (url shortcuts from windows) ?

I dont mind using a wrapper script if anyone knows of one ?

Cheers

---

### Post by Crc-3rr0r on 2006-10-23
So these forums dont look that active :

I've solved this by using gnome-actions plus this script I wrote

cat open-ie-shortcut 
#!/bin/sh

test -e "$1" || exit 0
cat "$1" | grep URL | cut -d'=' -f2 | xargs mozilla-firefox &

It's sucky but it works

---

### Post by PositiveK on 2008-05-21
> **Crc-3rr0r said:**
> So these forums dont look that active :

I've solved this by using gnome-actions plus this script I wrote

cat open-ie-shortcut 
#!/bin/sh

test -e "$1" || exit 0
cat "$1" | grep URL | cut -d'=' -f2 | xargs mozilla-firefox &

It's sucky but it works

Using the [FONT="Fixedsys"]cut[/FONT] command (esp. with the delimiter flag) is not what we want to do, because the URL itself may contain that delimiter (i.e. the "=" sign).

Here is a script I am now using until Gnome can support these .url files more obviously.  Note that this is based on your command above.  Thanks!!

```

#!/bin/sh

# Borrowed from http://ubuntuforums.org/showthread.php?t=282707

# Ask GNOME for the web browser command.
BROWSER=`gconftool-2 --get '/desktop/gnome/url-handlers/http/command' | cut -f1 -d' ' `

# 
E_NO_ARGS=65

if [ $# -eq 0 ]  # Must have command-line args to demo script.
then
  echo "Please invoke this script with one or more command-line arguments."
  exit $E_NO_ARGS
fi  

# Test for file existence.
test -e "$1" || exit 0

# Use sed to remove the first (known) part of the line.
cat "$1" | grep '^URL=' | sed 's/^URL=//' | xargs $BROWSER &

# Note: We should probably use "head" to just grab the first line resulting from the "grep", to be safer.
```

---

### Post by oomingmak on 2008-07-05
> **Crc-3rr0r said:**
> Hi how do get firefox to recognise url files (url shortcuts from windows) ?

A year ago, I made a step by step guide on how to do it. You can find it in the Ubuntu Archive, here:

[B][[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=495131[/COLOR]]("http://ubuntuforums.org/showthread.php?t=495131")

[/B]
I don't know why your search didn't show my thread in your search results.

---

