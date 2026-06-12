---
title: "find-grep-remove-entries"
date: 2009-01-12
forum: General Help
---

### Post by drboontu on 2009-01-12
Hi, :-)

I have a backup directory with backup files of my bash_history, is there a way to use find or grep to remove strings that are repeated many times in many files? e.g. "apt-get update".
Can I search many files at once and remove multiple entries?
It would be great if it is possible to create a file at the same time containing all the entries removed so I can check it is only removing the entries I want removed.

Cheers!
dave

---

### Post by sdennie on 2009-01-12
You could probably accomplish this with a uniq.  See:

```

man uniq

```

---

### Post by drboontu on 2009-01-12
Thanks!

That seems to be what I'm looking for. I have used this in the past to clean up one file at a time:

cat oldfile.txt | sort | uniq > newfile.txt

And this is how I'm searching the files:

grep update *

or:

find . -print0 | xargs -0 grep -H update

Now I need to find out how to mix the two commands, and end the command with something like: | tee /tmp/update.list

Cheers!
dave.

---

### Post by dagnabit dang doohickey on 2009-01-12
Bash history dupes can be controlled on the fly using the HISTCONTROL shell variable.
```
export HISTCONTROL=ignorespace:ignoredups:erasedups
```
ignorespace - lines that begin with a space character are not saved in the history list
ignoredups - lines matching the previous history entry are not saved in the history list
erasedups - removes all previous lines matching the current line from the history list before the current line is saved
ignoreboth - shorthand for ignorespace and ignoredups


You can also be more specific about which commands to ignore using the HISTIGNORE shell variable.

I use the following to ignore any command less than five characters:
```
export HISTIGNORE="!(?????*)"
```
Use a colon to separate multiple patterns:
```
export HISTIGNORE="ls:clear:touch*"
```

---

### Post by drboontu on 2009-01-14
Hi,

Very nice & thanks for the tips, I'll use them from today, but I still would like to find out how to clean up my backup files.

Cheers!
dave.

---

