---
title: "A way to distinguish between folders of the same name in Activities?"
date: 2020-11-04
forum: Desktop Environments
---

### Post by danwgrace on 2020-11-04
Hi, 
I'm fairly new to Ubuntu, but starting to get to grips with the interface. One thing I find annoying though is not being able to easily distinguish between two folders, in two instances of the Files app, of the same name, but in different locations.

For example say I have directories:
~/venvs/foo
~/venvs/bar

And both "foo" and "bar" contain a "src" directory. Using alt+tab to switch between folders quickly becomes quite confusing when there are several instances of Files open, including the two "src" directories for example. A better way is to right click Files on the Activities, click on "All Windows" and then choose the appropriate folder. This is OK, but means that you have to remember the order of the folders listed in this way. So I'm wondering if there is a way of giving a folder a long name in Files e.g. "foo/src", so that it can be easily distinguished? I'm surprised that Files doesn't add some sort of prefix when there are two windows with the same folder name.

---

### Post by TheFu on 2020-11-04
There are multiple different GUI file-managers on Linux - probably 20 - 50 of them.  Find one that shows the path you like to see or allows configuring it.  Most will support a 2-panel mode with the directories in the left and files in the right. There is a setting for that in caja and probably others. I don't use the GUI much, so don't really keep up with that. Sorry.

Regardless, to get good help, please state which Ubuntu release and which DE you are running, so people don't have to guess. GUI programs change with each release.

Some other ideas ... 

If you use a terminal with the default "prompt", then the path will be displayed in the prompt.  For example:
```
thefu@regulus:/etc/dconf/db$
```
or
```
thefu@regulus:~/Blog_PUB$
```

There are 3 parts to that bash prompt, this is the default, BTW:
[LIST=1]
[*]username
[*]hostname
[*]current working directory, CWD sometimes called PWD, present working directory
[/LIST]

This prompt is exactly the required format for use in scp and rsync commands too.  Very handy.

The first example shows /etc/dconf/db, which is an absolute path to a system directory.
The second example shows a directory under thefu's HOME - relative to that location.

Many programming tools require that a specific CWD be used to accomplish most tasks. This is how different projects are kept separate.  Windows people likely didn't learn this concept, though Windows has exactly the same idea about CWD.

---

