---
title: "Files to uppercase using rename"
date: 2009-01-26
forum: General Help
---

### Post by Gfy on 2009-01-26
I want to rename a bunch of files from uppercase to lowercase using the *rename* command. Here is a snippet from the man page:

>        To translate uppercase names to lower, you&#8217;d use

               rename 'y/A-Z/a-z/' *


But when I try it, I get the following error:

> $ rename 'y/A-Z/a-z/' *
UPPERCASE not renamed: uppercase already exists


Using -f, --force (Force: overwrite existing files.) gave no error, and the files are still in uppercase.

Is this a bug or am I missing something?
And how do I accomplish my task?

---

### Post by kaibob on 2009-01-26
Rename seems to work OK for me in the situation you describe:

> kaibob@dell:~/temp$ ls
TESTFILE  uppercase  UPPERCASE
kaibob@dell:~/temp$ rename --force 'y/A-Z/a-z/' *
kaibob@dell:~/temp$ ls
testfile  uppercase

---

### Post by e1mer on 2009-01-26
I don't know about rename, it sounds like it fails
renaming files to the same name.
I have always used the code below:

```

# to get the ^M type ctrl-v ctrl-m, not a carat and an M
set IFS='^M'
for ea in *; do
    if echo $ea | grep -q "[A-Z]"; then
        mv $ea `echo $ea | sed -e 's/A-Z/a-z/g' `
    fi
done

```

You may wish to use something other than * as the filespec.
The IFS (input field specifier) lets the filenames have spaces.

---

### Post by mb_webguy on 2009-01-26
You can do this very easily with GPRename, a GUI renaming utility in the repos.

---

### Post by Gfy on 2009-01-27
Thanks for the help guys.
I found the problem: I think it's a bug in Linux Mint that I'm using.

I tested it on a real ubuntu system and it worked like expected.


I tried using GPRename, but the error I got was more or less the same like 'UPPERCASE not renamed: uppercase already exists'.

Thread about this in the Mint forums.
[http://linuxmint.com/forum/viewtopic.php?f=47&t=21371](http://linuxmint.com/forum/viewtopic.php?f=47&t=21371)

---

### Post by geirha on 2009-01-27
Are you renaming files on an NTFS or FAT filesystem? In Windows filenames are partially case insensitive. If you create a file called "FOO", the name will be displayed as "FOO", but you can access it with "FOO", "Foo", and "foo" etc... so when you try to change "FOO" to "foo" it fails because "foo" already exists (as "FOO").

One way to get around this is to temporarily add an extra char in the filename, then rename back with the correct case:

```

# Add a - at the end of each filename
rename 's/(.*)/$1-/' *

# Turn uppercase to lowercase, and remove any ending -
rename 'y/A-Z/a-z/ ; s/(.*)-$/$1/' *

```

---

### Post by Gfy on 2009-01-27
Problem solved :)

I was working on my external drive and it's formatted FAT32.

---

