---
title: "[SOLVED] Finding *~ files."
date: 2008-05-31
forum: Desktop Environments
---

### Post by Barriehie on 2008-05-31
Hello!  I want to find all the files I've edited, i.e. all the ones ending with tilde.  I ran ```
ls -1lR /*
``` in a terminal to see if I had the recursion part down, (never done it before) and everything displayed correctly.  Now when I run ```
ls -1lR /*~
``` I get an error of no such file or directory.  Should I use the first command and then grep the generated file???  Is there a way to do this that will generate a text file containing only the files matching *~ ?

Thank You,
Barrie

Note: I'm a noob here and a bash book is on the list of things to get to insure against future -oops'-. :)  (had to reinstall once!)

---

### Post by mike2357 on 2008-05-31
I think what's going on is that when you enter the command:

ls -1lR /*~

You're telling ls to list files in the root directory that end in a tilde, plus recursively list all of the contents of directories in the root directory that end in a tilde.  In other words, the recursion doesn't mean search through all directories looking for anything that ends in a tilde.

To find anything, anywhere that ends in a tilde, try the following:

find / -name '*~' -print
This means:  Start at the root directory, recurse through everything, and list anything that ends in a tilde.


An alternative, if  you want more information is:

find / -name '*~' -exec ls \-ld {} \;
This means:  Start at the root directory, recuse through everything, and when anything ending in a tilde is found, run the command "ls -ld" on it.  The d means to just list directory names that end in a tilde rather than their contents.

Note that it won't enter directories where there is no permission, so you may have to precede the command with sudo.  While the find command is running (it may take awhile), run "man find".  It's a powerful command.

Good luck.

---

### Post by Barriehie on 2008-05-31
Thank you Mike!  I can now add 1 more command to the dozen or so I know and also this OS makes sense, again! :)

Barrie

---

