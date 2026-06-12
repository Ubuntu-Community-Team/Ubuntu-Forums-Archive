---
title: "&quot;ln -s&quot; requires full path"
date: 2009-01-18
forum: General Help
---

### Post by emakarov on 2009-01-18
Hello,

According to "man", the command "ln" has four possible forms. I have a problem with forms three and four:

```
ln [OPTION]... TARGET... DIRECTORY     (3rd form)
ln [OPTION]... -t DIRECTORY TARGET...  (4th form)
```

This seems to require that TARGET is an absolute path. For example, when I say

```
> ln -s $(pwd)/test.txt subdir
```
the result is as expected:

```
> ls -l subdir/test.txt
lrwxrwxrwx 1 emakarov 220 47 2009-01-18 16:12 subdir/test.txt -> /home/emakarov/test.txt
```
but when I say

```
> ln -s test.txt subdir
```
I get

```
> ls -l subdir/test.txt
lrwxrwxrwx 1 emakarov 220 8 2009-01-18 16:14 subdir/test.txt -> test.txt

```
in red font, which signifies a broken link. The problem is, I found nothing in the man page about this. Is it a bug in the program/documentation, or am I missing something?

Thank you,
Evgeny

---

### Post by mssever on 2009-01-18
There's no problem giving a relative path. The path will be interpreted relative to the current location of the symlink. Make sure that the symlink is pointing to a file that actually exists. The following works fine:
```
~:$ echo Hi > foo
~:$ ln -s foo bar
~:$ cat bar
Hi
```

---

### Post by emakarov on 2009-01-18
> **mssever said:**
> The path will be interpreted relative to the current location of the symlink.
You mean relative to the place where the symlink is created by this command, and not relative to the place where the command was issued? Yes,

```
> ln -s ../test.txt subdir/
> ls -l subdir/test.txt
lrwxrwxrwx 1 emakarov 220 11 2009-01-18 16:40 subdir/test.txt -> ../test.txt
```

seems to work... I still think this has to be described in the man page. The situation where the path is taken not relative to where the command is executed is unusual, to say the least.

Evgeny

---

### Post by mssever on 2009-01-18
It doesn't make sense to create the link relative to the current working directory, because that will change over time. If you move your symlink to another location, you'll notice that it's pointing to a different target. The only sensible way to make the link is to make it relative to its own directory.

---

### Post by jocko on 2009-01-18
I think you have to set either absolute path or path **relative to the link**, so:
```
ln -s ../test.txt subdir
```would make a link pointing to a file in the directory above subdir, while:```
ln -s test.txt subdir
```would make a link pointing to itself...

---

### Post by efalk on 2009-01-18
ln -s creates a symbolic link, which is very little more than an arbitrary string of characters.  For instance, you could very reasonably do

```
ln -s 'This directory is no longer in use, consult your manual' README
```

And the corresponding README entry would be created, completely irrespective of whether or not there's actually a file with that long name.

What makes symlinks special is that they can (and usually do) name another file on the system.  That other file's name is always taken relative to the directory where the symlink lives.  So the symlink to "test.txt" would be a symlink to test.txt inside the same directory.  The command **ln -s test.txt subdir** would create a symlink named test.txt pointing to test.txt, which you've already observed isn't very useful.

In general, to make a successful symlink, I find that it's easiest to cd to the destination directory and make the symlink from there, e.g.

```
cd subdir; ln -s ../test.txt .
```

Filename completion can be very useful here.

With a little care, however, it's not necessary.  You just need to be aware of what the symlink will mean relative to the directory you're creating it in.  For example, this command could be executed from anywhere because the destination directory is given as an absolute path:

```
ln -s ../init.d/foodaemon /etc/rc3.d/S88foodaemon
```

The above command will create the appropriate relative symlink from /etc/rc3.d to /etc/init.d even though I wasn't in either of those directories when I gave the command.

---

