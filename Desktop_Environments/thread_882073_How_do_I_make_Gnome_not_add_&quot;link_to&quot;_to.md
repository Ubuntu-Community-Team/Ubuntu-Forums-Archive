---
title: "How do I make Gnome not add &quot;link to&quot; to my links?"
date: 2008-08-06
forum: Desktop Environments
---

### Post by sicofante on 2008-08-06
In Windows there's a very easy way to NOT put the text "Shortcut to" in front of every newly created shortcut's name. This is for a good reason: it's VERY annoying to have that text always added by the system and it is redundant, since there's graphical info (an arrow) telling the user it is indeed a shortcut.

I was researching how to do this in Gnome, and I got to this thread:

[http://ubuntuforums.org/showthread.php?t=652979&highlight=link+to&page=2](http://ubuntuforums.org/showthread.php?t=652979&highlight=link+to&page=2)

but it's in the archives now (how come a thread with a 2 weeks old post is already in the archives and I can't reply to it anymore?)

So I'm basically reopening the issue: I hate Gnome adding the text "Link to" in front of all my links. The arrow emblem tells me it's a link, there's no need for additional information. I was hoping some gconf-editor settings would make it easy to change this redundant behaviour, but I can't seem to find it.

Any help would be very appreciated.

---

### Post by pauper on 2008-08-06
I can't quite understand from your post whether you aware of the concept of
symbolic linking or not, so if I'm making an assumption, please forgive me.

How does the underlying script supposed to know about what kind of name to
give to a pointer on itself? Fact: there couldn't be two files/directories
with identical names in the same directory. When you hold down Ctrl-Shift and
drag-and-drop some file to *other directory* it works as expected--keeps the
same name, unless, again, that name is already in use.

If you're complaining why "Link to <highlighted_filename>" and not
"<highlighted_filename>n", well, that's the choice of the author(s) or
maintainer(s). For a very fresh GNU/Linux user it's more intuitive to have
"Link to..." name other than "<highlighted_filename>n" and ponder about
emblem's profound meaning. There is no need to complicate the code with petty
options to have them both.

You will, likely, have to get the source code, rewrite and compile it yourself
in order to change that.

Try, for a change, copy and paste some file in the current working directory.

```
:~$ **mkdir ~/Desktop/foo**
:~$ **cd ~/Desktop/foo**
:~/Desktop/foo$ **touch file_1**
:~/Desktop/foo$ **cp file_1 file_1**
cp: `file_1' and `file_1' are the same file

# Here, in GUI, some script kicks in creating "file_1 (copy)" as the result.

:~/Desktop/foo$ **cp file_1 file_2**
:~/Desktop/foo$ **ln -s file_1 file_1**
ln: creating symbolic link `file_1' to `file_1': File exists

# Again no chance of having same names. GUI variant--"Link to file_1".

:~/Desktop/foo$ **ln -s file_1 file_3**
:~/Desktop/foo$ **ls -l**
total 0
-rw-r--r-- 1 ... file_1
-rw-r--r-- 1 ... file_1 (copy)
-rw-r--r-- 1 ... file_2
lrwxrwxrwx 1 ... file_3 -> file_1
lrwxrwxrwx 1 ... Link to file_1 -> $HOME/Desktop/foo/file_1
:~/Desktop/foo$ **mv Link\ to\ file_1 file_4**
:~/Desktop/foo$ **ls -l**
total 0
-rw-r--r-- 1 ... file_1
-rw-r--r-- 1 ... file_1 (copy)
-rw-r--r-- 1 ... file_2
lrwxrwxrwx 1 ... file_3 -> file_1
lrwxrwxrwx 1 ... file_4 -> $HOME/Desktop/foo/file_1
```

There is no way yet for an average computer to make that choice for you. And
why should it?
It's either using a single command, such as "ln -s <target> <linkname>", or
<right-click>-<Make-Link>-<Rename>.

I'm not familiar with creating links in Windows. Please, enlighten me on that
subject.

---

### Post by sicofante on 2008-08-07
I'm somewhat new to Gnome/Ubuntu but very old to Unix. I know it all about symlinks or hard links.

The right behaviour can be very well illustrated if we change the word "link" to "copy" in this discussion. Please check how copies are made and voila.

If the copy is made inside the same directory, the newly created file receives a "(copy)" text appended to its name. If you copy a file from one directory to another, no text is appended to the new file's name. Just apply the same logic to links and everybody will be happy.

Is the arrow emblem not enough information? I think that of course it is, after you have created your third link you'll know what it means. But it you want more, non-intrusive info about the file, how about hovering about it and getting a tooltip on what that is? Just an idea.

Even fresh users get annoyed by this "Link to" text after a couple of weeks. It is not a good idea and when comparing it with the copy operation behaviour, it's not even consistent.

PS: Remember we're not talking about the command line interface, but the Gnome desktop environment and how it manages copies and links.

---

### Post by pauper on 2008-08-07
Well, how often do you create symlinks inside of the same directory and keep
those links' names unchanged?

Let say you would like to have the same icon for all terminal emulators:
by default you supposed to keep all such custom icons in some ~./icons/.../apps
directory and point them to "utilities-terminal.svg". Now if you use point-click
method, you'll end up with bunch of copies of "utilities-terminal (copy).svg"
(suggested? by you) or "Link to utilities-terminal.svg" (current). What's your
next step would be? Rename them to "gnome-terminal.svg", "konsole.svg", etc.

Explain me the purpose of creating some reference point and keeping it as such,
but not changing it to some valid alias (not a reference to "alias" bultin).

Creating symlinks between files/directories in different directories would work
as expected, i.e. will duplicate the original name to symlink, unless that name is 
already occupied (fallback to "Link..." or "... (copy)").

I don't see any benefit behind changing the default scheme. Why bother fixing
something that is not broken.

> **sicofante said:**
> The right behaviour can be very well illustrated if we change the word "link"
to "copy" in this discussion. Please check how copies are made and voila.

If the copy is made inside the same directory, the newly created file receives
a "(copy)" text appended to its name. If you copy a file from one directory to
another, no text is appended to the new file's name. Just apply the same logic
to links and everybody will be happy.

I disagree. There has to be a visual diversity. My example with "copy" is only
to show that there is no place for identical names under one directory.
Comparing "copy" to "ln -s" is like comparing apples to oranges.

[color=blue]cp[/color]: different inodes; all are "physical" files; any changes done to either/any
don't reflect on the rest, unless removing mutual parent directory.

[color=blue]ln[/color]: one inode; all are "physical" files; anything done to either/any is
inherited by the rest, except deleting, and on the contrary, removing mutual
parent affects all.

[color=blue]ln -s[/color]: different inodes; only original is an actual file, the rest are but
references to it (i.e. /path/to/original); remove original--the rest are kept,
but broken, remove reference--original and the rest, if any, are intact, only
that particular path to original is broken; removing mutual parent affects all.

Regards.

---

### Post by sicofante on 2008-08-07
> **pauper said:**
> Creating symlinks between files/directories in different directories would work
as expected, i.e. will duplicate the original name to symlink, unless that name is 
already occupied (fallback to "Link..." or "... (copy)").

Sorry but you're wrong here and since this is the whole point of the discussion, I think the rest is of no real use. (Meaning all that long lesson about the differences between cp, ln, ln -s, etc. and all what happens when linking to the same directory is just out of place.)

Creating symlinks between files/directories in different directories puts the words "Link to" before the name of the link. It will NOT just duplicate the name of the original file, as you wrongly state, no matter if that name is already occupied or not. THAT is what's bothersome, precisely.

Please check your Gnome behaviour before continuing the discussion. And remember we're not talking about command line here: just use middle click drag and drop and when you release your button, select "Link" from the menu you're offered with.

---

### Post by pauper on 2008-08-07
:shock:

---

### Post by sicofante on 2008-08-07
Wow, that's a lot of work just to say "I'm using an older version of Gnome where this doesn't happen", but thanks anyway. Please understand that normally people are referring to current versions of the software. Otherwise they state that in their first posts.

So the issue remains: current Gnome has undone what was properly designed in version 2.20. Going back to the beginning of the thread.

---

### Post by pauper on 2008-08-07
I poked around with Live CDs. Here are my findings:

It works as I described in Nautilus 2.18.1 (feisty), 2.20.0 (gutsy). And you're
right about Nautilus 2.22.2 (hardy). Later releases?

I don't know why would they change that.

The [bug report](http://bugzilla.gnome.org/show_bug.cgi?id=534432) was filled out on 2008-05-23 and *there's patch provided*.
Have you tried it?

---

### Post by sicofante on 2008-08-07
Thanks for the info. How do I apply that patch?

---

### Post by pauper on 2008-08-08
Well, highlight the text...

> diff -up

...

dest = get_target_file_for_link (src, dest_dir, count);

Paste in editor, and save as something like "symlink_no_append.patch".

Get the tools for compiling and patching:

```
sudo apt-get install patch build-essential
```

Get nautilus' source code. By the way, you can get it from [here](http://ftp.acc.umu.se/pub/GNOME/sources/nautilus) as well.

```
:~$ **cd ~/Desktop**
:~/Desktop$ **apt-get source nautilus**

# Or if you need some particular version:

:~/Desktop$ **apt-cache showsrc nautilus**
:~/Desktop$ **apt-get source nautilus=1:2.20.0-0ubuntu7.1**

# Compare source code version and one mentioned in the patch file header,
# if needed, rename the version in the path name.

:~/Desktop$ **mv symlink_no_append.patch nautilus-2.??.?/ && cd nautilus-2.??.?/**
:~/Desktop/nautilus-2.??.?$ **patch --dry-run -p1 -i symlink_no_append.patch**
```

Note: You might need to play with -p? value.

Now, if lines don't match it will spit out...

```
patching file libnautilus-private/nautilus-file-operations.c
Hunk #1 FAILED at 240.
Hunk #2 FAILED at 253.
Hunk #3 FAILED at 4294.
3 out of 3 hunks FAILED -- saving rejects to file libnautilus-private/nautilus-file-operations.c.rej
```

But, since it's a dry-run no actual *.c.rej is created. Run again without
-dry-run parameter to generate one.

On successful run it tells that patching is being done:

```
patching file libnautilus-private/nautilus-file-operations.c
Hunk #1 succeeded at 240 (offset -40 lines).
Hunk #2 succeeded at 253 (offset -40 lines).
Hunk #3 succeeded at 4212 (offset -141 lines).
```

Don't forget to apply actual changes:

```
:~/Desktop/nautilus-2.??.?$ **patch -p1 -i symlink_no_append.patch**
:~/Desktop/nautilus-2.??.?$ **rm symlink_no_append.patch**
```

If all fails, quit this masturbation with patching and edit file manually.
Look at the patch file header: "--- /path/to/file_1" and "+++ /path/to/file_2",
change any "-" string value to "+", or vice versa, in the original file.

Now, the fun part--compiling: read README and INSTALL files for further actions. 

Since you're running current nautilus version, I guessed it's 2.22.4, and
attached updated patch, based on the original from [the link](http://bugzilla.gnome.org/show_bug.cgi?id=534432). Remove *.txt
extension.

---

### Post by sicofante on 2008-08-08
Well, thanks again for all your effort. I guess I'll wait until someone finds a way to binary patch this or Gnome devs go back to the very reasonable old behaviour. My programmer abilities are very rusty and I might revive them one of these days, but not yet.

---

