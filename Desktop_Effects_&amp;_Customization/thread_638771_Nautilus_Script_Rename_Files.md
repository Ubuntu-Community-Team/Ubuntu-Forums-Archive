---
title: "Nautilus Script Rename Files"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by badman3k on 2007-12-12
I'm trying to find a nautilus script that will allow me to rename single/multiple files by prefixing the original file name with "VIEWED".

I am afraid I'm not really familiar with Bash scripts, how they work or what the best commands are. I've found that there are two possible ways that the above could be done:
1) Rename command and some regex
2) Move command and just prefix the original name with "VIEWED"

Any help would be appreciated

Richard

---

### Post by unholy1 on 2008-05-28
From [http://jrfonseca.blogspot.com/2006/05/mass-renaming-in-nautilus.html:](http://jrfonseca.blogspot.com/2006/05/mass-renaming-in-nautilus.html:)
> One can easily add new actions in Nautilus context menu by adding shell scripts to ~/.gnome2/nautilus-scripts . Below is a script for mass file renaming, using Perl's rename utility and zenity. Add it to ~/.gnome2/nautilus-scripts/Mass Rename.

#!/bin/sh
# Nautilus script for mass file renaming

set -e

TITLE=`basename "$0"`

# Path to perl's rename
RENAME=/usr/bin/rename


rename_all() {
        IFS=$'\n'
        for FILE in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
        do
                cd "`dirname "$FILE"`"
                "$RENAME" "$@" "$EXPR" -- "`basename "$FILE"`"
        done
}


EXPR="s///"
while true
do
        EXPR=`zenity --title "$TITLE - expression" --entry --text "Specify the Perl expression for modifying the filenames." --entry-text "$EXPR"` || exit

        rename_all -n | sed -e 's/^\(.*\) renamed as \(.*\)$/\2\n\1/' | zenity --list --width 800 --height 600 --title  "$TITLE - Preview" --text "" --column "New name" --column "Old name" && break
done

rename_all


---

### Post by unutbu on 2008-05-28
You might also want to check out the pyrenamer package (its in the official repos).

```
% apt-cache show pyrenamer

Description: Mass file renamer written in PyGTK
 You can rename files using patterns, search and replace,
 substitutions, insert or delete text, or even rename
 files manually.
 You can also rename images using their EXIF tags
 and music using their internal tags.
 .

```
Homepage: [http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

---

