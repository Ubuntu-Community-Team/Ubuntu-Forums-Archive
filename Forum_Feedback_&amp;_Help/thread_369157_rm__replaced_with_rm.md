---
title: "rm *** replaced with rm *** ???"
date: 2007-02-24
forum: Forum Feedback &amp; Help
---

### Post by HadroLepton on 2007-02-24
i have noticed that "rm ***" are being replaced with "rm ***"

for example here
[http://ubuntuforums.org/showthread.php?t=282344](http://ubuntuforums.org/showthread.php?t=282344)
and here
[http://ubuntuforums.org/showthread.php?t=368869](http://ubuntuforums.org/showthread.php?t=368869)

and here
```
rm *** directorynametodelete
```

why is that?
when some poor newbie follows the instruction if will delete all his files instead of the directory.

---

### Post by highneko on 2007-02-24
Recently in another forum I noticed something similar. I like to beat a system. It's a good idea tho.
rm -r[COLOR="Black"]f> [/COLOR] /nothing #zomg, hax!

---

### Post by PriceChild on 2007-02-24
We're aware of the issue.

Was intended to remove just the "rm *** /" command but things went a bit wrong... :) Will have it sorted out soon I'm sure.

---

### Post by highneko on 2007-02-24
I heard once that a rm was editing so that wasn't possible. Couldn't they create a bash script to prevent this? Maybe something like this:
```
#!/bin/bash
if [[ "$@" != "/" ]]; then
echo "rm -r[COLOR="Black"]f> [/COLOR] $@"
fi

```

---

### Post by PriceChild on 2007-02-24
All fixed afaik

---

### Post by matthew on 2007-02-24
The problem existed because I was playing with the language filter to see if we could keep jokers from telling people to type "rm -rf /"

It didn't work out well. Sorry for the confusion. I think we will just have to go back to reminding people in threads where this is posted not to type commands they don't understand.

---

### Post by highneko on 2007-02-24
It's a good idea. Just the -rf part on a regular directory might do things the user wouldn't want. 

Just so everyone knows how it's used:
```
       -f, --force
              ignore nonexistent files, never prompt
       -r, -R, --recursive
              remove directories and their contents recursively
```
Here's some unrelated but useful information too:
```
To remove a file whose name starts with a `-', for example `-foo',
use one of these commands:
  rm -- -foo

  rm ./-foo
```
It's always a good idea to read the man page first. n_n

---

### Post by HadroLepton on 2007-02-24
thanks for clearing this up.
i know you mean well, but censorship is never a good solution.

---

