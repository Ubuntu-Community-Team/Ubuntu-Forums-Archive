---
title: "bash wildcard question"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Westerberg on 2006-08-05
Lets say I have a directory with 60 files.  Twenty of the filenames end in "abd", 20 end in "dba", and 20 end in "bad".  I want to list all the files that don't end in "abd".  What would be the CLI command to accomplish this?

---

### Post by ardchoille on 2006-08-05
You can do:  ls /path/to/files/*.{dba,bad} and that will list all files that don't end in .abd. You can use any number of extensions within the brackets, like so: ls /path/files/*.{abd,txt,mpg,mp3}.

---

### Post by drlock on 2006-08-05
If you do not know the list of all acceptable extensions you can do this:
find . -name '*.abd' -prune -o -print

This matches all files ending with 'abd' and then discards them and returns the rest.  You can do lots of cool stuff with find, like execute a command on each file you match:

find . -name '*.abd' -prune -o -exec touch {} \;

This will make all non-abd files have the current time for a modification date, you can of course replace touch with any other bash command.

---

### Post by ardchoille on 2006-08-05
> **drlock said:**
> If you do not know the list of all acceptable extensions you can do this:
find . -name '*.abd' -prune -o -print

This matches all files ending with 'abd' and then discards them and returns the rest.  You can do lots of cool stuff with find, like execute a command on each file you match:

find . -name '*.abd' -prune -o -exec touch {} \;

This will make all non-abd files have the current time for a modification date, you can of course replace touch with any other bash command.

Nice. I'm wondering if there is a tutorial or something for manipulating extensions.

---

