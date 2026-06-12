---
title: "xterm use current directory"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Wally68 on 2005-11-16
Greetings all. I'm trying to setup rox-filers "Set Run Action" for *.rar files to extract into the same directory as the rar files reside. Here's the command I'm currently using:
```
xterm -hold -e unrar e "$@"
```
This command works, but extracts the file into ~/, which is a hassle. There must be a way to make xterm run in the current directory instead.


      Thanks
                   Wally


Edit: coorected spelking mistales.

---

### Post by Ampersand on 2005-11-16
Is there anything in the man page for unrar? I don't have it installed at the moment so can't check, but there should be a switch for setting the directory it extracts to. Using this with . as the directory might help (and if it doesn't, at least it's bumped your thread a bit (: )

---

